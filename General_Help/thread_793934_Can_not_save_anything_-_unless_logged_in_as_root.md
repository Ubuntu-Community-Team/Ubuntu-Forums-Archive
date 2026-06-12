---
title: "Can not save anything - unless logged in as root"
date: 2008-05-14
forum: General Help
---

### Post by jimbob21 on 2008-05-14
I have just upgraded from Gutsy to Hardy and not I can only save files when logged in as root.

If I create any file using Gedit, open office, Gimp (Image editor), when I click save, the programs automatically close.

However, when I go to terminal and click

sudo nautilus /usr/share/applications/

then I can open up applications from there and save files.
The same thing occurs when I click "Open" also.

How can this be resolved?

---

### Post by misterspider on 2008-05-14
Who is the owner of your home directory?
Look in Nautilus for your folder in /home directory, right click your folder and look at properties, permissions tab.

If owner is root, you can open a terminal and use

cd /home
sudo chown user_name /user_name

---

### Post by bobblehat on 2008-05-14
Sounds like a file ownership/permissions problem. The first thing to check is that you're the owner of files and directories in your home directory and below. One possible cause of that's manually copying all your files from one user to another or one installation to another and ending up with them owned by the wrong user.

The link below gives instructions on how to view and change owner and permissions.

[http://library.gnome.org/users/user-guide/stable/gosnautilus-8.html.en](http://library.gnome.org/users/user-guide/stable/gosnautilus-8.html.en)

I hope that helps.

---

### Post by jimbob21 on 2008-05-14
There is only one user account on the system and the user is the owner of the home folder.  The folder access is also set as "Write and Read" access.  

Any other suggestions ?

---

### Post by chrisccoulson on 2008-05-14
Please do a 'ls -l' in the folder that contains the files you are trying to edit. That will be easier to interpret.

---

### Post by jimbob21 on 2008-05-14
Sorry, let me clarify.  If I open a file by double clicking on it and save it works fine.  

If I open up a application and:

1)  click the open button...or
2)  create a new document and then I press the save button

Both these actions cause the application to automatically close, unless I have open the application as root.

---

### Post by chrisccoulson on 2008-05-14
Thanks for clarifying that. Could you launch the application from the terminal as a normal user, attempt to save, and then post the output to the terminal here.

---

### Post by jimbob21 on 2008-05-14
I am not sure if this is what you mean, but i typed

gedit

in terminal which opened up gedit.  I then typed something and attempted to save.  When I did this, gedit automatically closed like usual, and terminal said

Segmentation fault

However, if I type

touch /home/user/test.txt

it will create the file.

Is this helpful ?

---

### Post by chrisccoulson on 2008-05-14
Yes, thank you.

Are there any crash reports in /var/crash? If so, you should submit the relevant report to Launchpad by double clicking on the crash report in Nautilus.

If there isn't one, then you may need to enable Apport. You can enable Apport by editing /etc/default/apport, and changing 'enabled=0' to 'enabled=1'. Then restart Apport by doing:
```
sudo /etc/init.d/apport restart
```

Then repeat the crash, and hopefully you will get a crash report

---

### Post by jimbob21 on 2008-05-14
I do have a crash report there, but it is for firefox.  I don't think that is a relevent report to the problem I am having.

I have turned apport on and restarted it, however, after the application closes down due to an attempt to save, no new crash report appears in /var/crash

---

### Post by gperezbrun on 2008-07-06
people:
          when ihttp://ubuntuforums.org/images/editor/menupop.gif upgrade my ubuntu to 8.04 the same thing happend to me. I was looking for this solution for months on Internet, but did not find it. That's why i start trying to fix it by my self (my skill is really low). the solution was:
[LIST=1]
[B][*] Do an adduser to create a new one.
[*] Copy the .gtk.bookmarks file from the new user to my regular user.
[*] Continue enjoing muy ubuntu. ;-)[/B]
[/LIST]

I hope that this can help everyone with this bug.

Gonzalo Pérez Brun.

---

