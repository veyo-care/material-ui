# Veyo-care/material-ui fork

This fork allows us to change material-ui components as we see fit. This repo works in parallel with the ```material-ui-built```repo.

## How to modify a material-ui component

1. Clone the ```veyo-care/material-ui```and ```veyo-care/material-ui-built```repos.

2. Go to your local version of ```material-ui``` and find the component you need to modify in ```/src```. Change stuff.

3. Open ```package.json``` and update the minor number of the version of the package.

4. Run ```yarn run build``` and then commit your change to the remote branch ```selectors```. 

5. Copy-paste the newly created ```build``` file to ```material-ui-built```with ```cp -r ./built/* ../material-ui-built```. 

5. If you just wanted to amend your last commit with a small fix, the ```build-amend```script runs 4. and 5. in a row with ```commit --amend --no-edit```. 

6. Go to ```material-ui-built``` and commit the new changes to ```master```. Similarly, if you just need to amend you can run ```push-built```. 

7. Go the environment where you launch your app. In all ```package.json```files containing a reference to ```material-ui```in the dependencies, rewrite the line to ```"material-ui: veyo-care/material-ui-built",```.

8. Run a ```yarn upgrade```. It would seem more logical to just run ```yarn upgrade material-ui```, but for some reason, if you do run this, yarn will behave as if you had typed ```yarn upgrade```anyway.  

9. You may have to rebuild your app.

## Troubleshooting

### I did everything but nothing has changed in my app and no error has been declared.
Make sure to update the version of the package in the ```package.json```file in ```material.ui```. Else, when running the ```yarn upgrade```command, yarn won't see that the module has been updated.

