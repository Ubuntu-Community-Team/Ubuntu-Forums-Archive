---
title: "Package Manager Error"
date: 2007-07-05
forum: General Help
---

### Post by Alucard_Duskmoon on 2007-07-05
Every time I try and run the update manager I get this error.
```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'wget' is not known on line 48 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
```
This is really ticking me off because I can't install anything until it's fixed.
If anyone else has this problem or knows how I can fix it please post. Also, I'm a bit of a newbie when it comes to linux so if I ask you to simplify somthing please do not get upset with me.
Thanks

---

### Post by McNils on 2007-07-05
Check line 48 in /etc/apt/sources.list. It seems to be starting with wget.  Lines in /etc/apt/sources.list shuold be a comment (start with #), deb* or be a blank line.

---

### Post by Alucard_Duskmoon on 2007-07-05
So basically, open it in text editor, on the 48th line change it so it follows one of those rules?

---

### Post by Alucard_Duskmoon on 2007-07-05
I don't think I can do that though. *I'm still used to doing everything the windows way*

---

### Post by Alucard_Duskmoon on 2007-07-05
If I edit it and attempt to save it gives me a "you do not have permissions". How would I avoid that?

---

### Post by scragar on 2007-07-05
you won't be able to edit it normaly unless you use the terminal to grant write privileges to the group, so open up the terminal and either copy and paste this in or type it out:

```
sudo chmod g+w /etc/apt/sources.list
```
and enter your password when prompted, then open up computer from the places menu, enter the "etc" folder, then "apt" and right click on "sources.list" and pick open with other application and scroll down around 4/5 of the box to text-editor, then go down using the line count till you find number 48 and just put a # in front of it for now(post the full lineup here so we can check what it should be), save and quit(you'll get a weird message about being unable to back it up, just choose yes).

next time you start package manager it shouldn't throw an error.

---

### Post by McNils on 2007-07-05
You need root permissions to edit the file. Press Alt-F2 and type gkudo gedit. (Or kdesu kate if you are running kubuntu). If you do this at the command line type
sudo nano /etc/apt/sources.list

---

### Post by Alucard_Duskmoon on 2007-07-05
Ok, should be fixed now. Thanks for the help

---

### Post by Alucard_Duskmoon on 2007-07-05
I saved it to another directory, deleted the un-edited one and moved the edited one to /etc/apt/
I guess it worked.

---

