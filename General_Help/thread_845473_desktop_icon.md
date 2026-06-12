---
title: "desktop icon"
date: 2008-06-30
forum: General Help
---

### Post by Zion420 on 2008-06-30
I am reletively new to scripting and have a mystery here. I have written a small script that will create a main directory and 3 sub dirs inside when the icon is clicked. If the main doesnt exist, and is created, I want a link or shortcut to popup on the desktop. How do I accomplish this, if at all. Thanks in advance.

---

### Post by ModelM on 2008-06-30
I think this is what you're after...

Just after the code creating the new directory, add the code to create the symlink, something like this...

```
...
else
    create new_directory
    #
    # This next line will create a symlink on the desktop
    # pointing to the directory just created
    #
    ln -s new_directory /home/my_home_directory/Desktop/new_directory

endif
...
```

---

### Post by Zion420 on 2008-06-30
:D Thank you very much. I looked all night last night and saw nothing that pointed me toward symlink. Probably pretty elementary to experienced programmers, but to me its like finding a new piece to this puzzle. WOOHOO, a new toy, lol thx again. :D

---

### Post by ModelM on 2008-07-01
Okay, I'll give you one more. In your original post you used the word "link". You knew what you wanted but were unsure how to go about it.

The next time you're in that situation the command "apropos" is your friend. For example, if you had typed:

apropos link

up would have popped a list of all commands related to the word "link". And "ln" is right there on the list.

If I want to rename a file but don't remember the command

apropos rename

would put me right in a jiffy.

How's that for a household hint?

---

### Post by Zion420 on 2008-07-01
Thats a great household tip, especially to a unix noob like me. I have been tinkering around with the code you provided, and it definitely pointed me in a great direction. Is there a way for the shortcut/link to pop out to the desktop. I may have gotten off track, I can get the link to show up in folders, just not materialize out on the desktop. One better, once I finally get it to the desktop is there a way to include in the script a different icon? So now it pops up there, and is sporting a custom icon?? I know I am close,....just not sure how close.

---

### Post by ModelM on 2008-07-01
I don't understand why it wouldn't appear on the desktop. I just typed this line into a terminal window:

 ln -s /etc/ppp/ /home/teeuu/Desktop/test

and got a folder icon on the desktop named "test" (with an arrow symbol indicating it is a link) pointing to the /etc/ppp directory.

I don't know why it wouldn't work as long as your script has write permissions to the Desktop directory.

---

### Post by Zion420 on 2008-07-01
lol thats awesome, thank you. Do you also know how to specify a particular icon to use in place of the defaults? Not that important, just seems that could also be useful in the future, and would put some icing on this cake here. lol a lil dry, thanks again.

---

### Post by ModelM on 2008-07-01
Nope, I don't know that trick.

---

