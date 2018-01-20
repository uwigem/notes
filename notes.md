---Notes to admin---
If you have any questions, I may or may not be able to answer them, but shoot me an email (andrewhu AT uw)

#PHP/HTML

The public_html folder is displayed at 
    http://students.washington.edu/uwigem/

The php files get their contents from their respective files in the src folder.
Just copy tmeplate.php and change the `<?php echo file_get_contents(); ?>` call.

#MySQL

MySQL is on Port 3034
The MySQL root password is this user's password EXCEPT that each character's ASCII value is decremented by 1
This is actually just to prevent bash from misinterpreting one of the characters in the password since there is a special character

So, if the user's password was "cdef9" the MySQL password would become "bcde8"
'

#Console Quirks

All the shell commands in ~/.bashrc are run when the connection is initialized.
Here, we have custom aliases (so you can pretend that MySQL is installed in the correct place)

If you get a problem where vim or another text editor writes the character '^?' when you press backspace, make sure that the command `stty erase '^?'` is in .bashrc

If you think .bashrc is not getting run, then make sure that 
```
if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
fi
``` is in .profile

Gitignore isn't working! All you have to do is add all the changes you *want* to track,
like .gitignore and any changes you don't want to lose. Now, commit them, so that
you won't lose them, *just in case* something goes wrong

Now naveigate to the top-level directory of the repository (the one with the .git and
.gitignore file). On this console there is a bash shortcut to the nearest top level
directory if you type `cdgit`. Finally, run these commands
```
git rm -r --cached .
git add .
git commit -m "Removing gitignore'd files"
```
"
The first, removes all indices of all files in the repo
The second, adds all the files back in, except the ones listed in .gitignore
The third commits the removals

#Git

##Pushing to Github from Vergil/Attu

The git settings on the UW servers can be different than the ones
at home, most notably, how they won't save your login information, or
even ask for it if you're trying to push. Leaving you without push access

So, we need to set up the account information. This guide will go over
HTTPS pushing. Normally, when you clone a repo, it goes

`https://github.com/user/repo.git`

Instead, what we want to do is clone it from this URL

`https://username:password@github.com/user/repo.git`

Don't be worried about exposing your password, since this will only be stored
in the .git directory, which is not pushed to the remote

If you've already made the repo and want to change the remote url, use the command

`git remote set-url origin https://github.com/USERNAME/REPOSITORY.git`

##Getting git to recognize your user

However, even if we do this, and push correctly, Github still won't recognize
us as the user we authenticated as! That's because we have the wrong email.
Vergil will automatically set your git email to a vergil email, instead we need
to change it using 

`git config --global user.email "email@example.com"`
