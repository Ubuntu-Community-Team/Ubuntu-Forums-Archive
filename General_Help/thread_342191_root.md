---
title: "root?"
date: 2007-01-19
forum: General Help
---

### Post by Ross M on 2007-01-19
This is the first time I've used Ubuntu in a very long time...I just installed it on a different computer (which I'm on right now) and when I installed it, there was no prompt for a root password (that I can recall), and whenever I try to log in as 'root' and not 'Ross', it asks me for a password which I obviously don't have.

Any help is appreciated.

Thanks,

Ross M

---

### Post by dorcssa on 2007-01-19
Have a look at this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) ;)

---

### Post by bodhi.zazen on 2007-01-19
> **Ross M said:**
> This is the first time I've used Ubuntu in a very long time...I just installed it on a different computer (which I'm on right now) and when I installed it, there was no prompt for a root password (that I can recall), and whenever I try to log in as 'root' and not 'Ross', it asks me for a password which I obviously don't have.

Any help is appreciated.

Thanks,

Ross M

Ubuntu uses sudo

sudo <command>

To change to root:

sudo su

OR

sudo -i

to set root PW:

sudo passwd

---

### Post by Ross M on 2007-01-19
I'm trying to insert userContent.css to my Firefox profile...but I get this error:

> you do not have permissions to change it or its parent folder

Any ideas?

---

### Post by taurus on 2007-01-19
What's the command that you ran?  Try to place a sudo in front of it.

```
sudo **command**
```
(Use the same password that you use to log in.)

---

### Post by Ross M on 2007-01-19
Hehe...I'm using the GUI, not Terminal =/ Not that smart with Linux yet.

---

### Post by taurus on 2007-01-19
<Alt>F2 -> gksudo nautilus

---

### Post by Ross M on 2007-01-19
What am I supposed to do with that?  I tried to run my .css file to try and save it, but no luck.

Sorry if my noobiness is brushing off on you lol...

---

### Post by taurus on 2007-01-19
Can you describe in more details what exactly are you trying to do?

---

### Post by Ross M on 2007-01-19
I'm trying to edit userChrome.css in /etc/firefox/profile/chrome/

But I don't have the right permissions to edit/rename/move/delete/etc.

---

### Post by ciscosurfer on 2007-01-19
> **Ross M said:**
> I'm trying to insert userContent.css to my Firefox profile...but I get this error:



Any ideas?If you Firefox profile is located in your Home directory, then you shouldn't be getting this error--everthing located here is under your username and you rights (permissions) to access everything.

When you get to your directory (which will be located here:```
 /home/<YourUsername>/.mozilla/firefox/<randomeLetters&Numbers>.default/chrome/
```Right-click the file, choose Open With > Open with Other Application > click the drop-down at the bottom (use a custom command) and type in **gedit**.

If you want to set this up permanently, right-click the file, choose Properties > click the Open With tab > click Add > use custom command > enter in **gedit**.  Then select it in the main properties/Open With tab, this will ensure that that gedit opens all files ending in .css

Hope that help! :D

---

### Post by taurus on 2007-01-19
> **Ross M said:**
> I'm trying to edit userChrome.css in /etc/firefox/profile/chrome/

But I don't have the right permissions to edit/rename/move/delete/etc.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/firefox/profile/chrome/userChrome.css
```

---

### Post by ciscosurfer on 2007-01-19
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo gedit /etc/firefox/profile/chrome/userChrome.css
```@Taurus and @Ross M,
If I'm not mistaken, doing it this way will make the change universal, across users.  Is this the intended result?

---

### Post by Ross M on 2007-01-19
My firefox isn't located in the /home.  All I have in /home is Destop, Examples, and a core file....I'm using the firefox that came with the lastest installation of Ubuntu.

Also, I just realized that userChrome.css is userChrome-example.css.  Is there a way to rename?

Thanks for the help guys :D

---

### Post by taurus on 2007-01-19
./mozilla is a hidden file so to see it, you have to run this command from a terminal.

```
ls -la ~
```

---

### Post by Ross M on 2007-01-19
Nothing became 'unhidden' lol

---

### Post by Ross M on 2007-01-19
Any ideas?

---

### Post by ciscosurfer on 2007-01-19
> **Ross M said:**
> Any ideas?Go into Nautulis (Places > Home Folder) and hit CTRL-H and this will show your hidden files.  Then refer to my original post as to where the files are located.

If you want to edit the files globally (accessible by all users on your computer) then modifying them under /etc/firefox... is the way to go and you can modify them by hitting ALT-F2 and in the box that pops up, enter in **gksudo nautilus** and this will bring up a Nautilus window with root permissions so you can edit the file.

Otherwise, modify the file located in the other path I mentioned in my first post.  This will make the modifications good for the user that is located in whichever username path you select (from above).

---

### Post by Ross M on 2007-01-19
They're not hidden, I just don't have the permissions....

And this is the firefox that's globally installed...

---

### Post by ciscosurfer on 2007-01-19
> **Ross M said:**
> They're not hidden, I just don't have the permissions....

And this is the firefox that's globally installed...You're not quite following what I'm saying: the user you are currently using has a hidden directory in your home directory called **.mozilla** (which you can get to by clicking **CTRL-H**).  If you dig down into that directory, you will the find the files I'm talking about.  Refer to my previous posts to get there.

The files located in **/etc/firefox...** are not hidden, and they are not owned by you, they are owned by root, so that's why you have to use **sudo gedit** **<path_to_files>** to modify those files or use **gksudo nautilus **to open a root-nautilus window and modify them that way.

Firefox always gets installed this way, unless you specify differently.  It has files located under **/etc** that are used by your entire system, globally.  And you have a local directory that references your logged on user, where your bookmarks, passwords, etc., are stored, and they are located under your hidden directory in your home directory called **.mozilla**

---

### Post by Ross M on 2007-01-19
Got it, thanks bro, I owe you one...if I ever get good at this lol :)

---

