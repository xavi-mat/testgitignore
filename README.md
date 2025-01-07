# TEST GITIGNORE

## Use case
Programming a React app, makoing builds and converting into an Android app with Capacitor.
By default, the `/build` and `/android` folders are ignored.
But, sometimes, we need to manually modify some configuration deep inside the `/android` folder.
Those modified files are not tracked by git.
We need git to track those modified files, and only those, deep inside an ingored folder that contains, also, `.gitignore` files that also ignore subfolders, and so on.

## Conclusion
When ignoring with `/foldername`, git won't bother to look inside the folder. Other `.gitignore` files in that folder won't be read.

We could "unignore" the **folder** and immediately ignore the **contents of the folder**:
```
/somefolder  # Original ignore pattern, created by default

# Add more lines at the end:
!/somefolder     # Don't ignore the folder
!/somefolder/**  # Ignore its contents
```  

Or just change the original `/somefolder`  to `/somefolder/**`.

Then, we need to go to that folder and repeat the process in a `.gitignore` file: "unignore" the subfolder (where the file that we want lies), and ignore **its contents**.
Repeat for every subsubfolder to reach the desired file, and only then, it can be unignored.
