---
title: "grub is on a separate boot partition- backup and splashscreen issue"
date: 2008-01-18
forum: General Help
---

### Post by streamsanddragonflies on 2008-01-18
Yep! Just when I think I know my way around a bit more, I find myself still with my head swimming and I am sure I am misinterpreting the help files or docs.!

I wanted to change my timeout for grub but from the command terminal.  So I accessed it with sudo gedit /boot/grub/menu.lst and just changed the time from 10 to 30 and saved the file...  I read that I should do an update-grub but I have done saved to file from the terminal before.  I thought that with gedit , acting as an extention to the terminal, I could thus save to file as well instead of this update-grub command that I have not used yet.

The other confusion is how to back up and insert a  boot splashscreen from the menu.lst properly -when I have a separate boot partition.  ( I have 4 operating systems on 2 drives- the MBR and /boot and linux files are on the primary drive)
The docs and posts say that there will be a problem with update-grub as it will think my root is in my boot drive.  Both my / and /home files share one partition.  The docs say to make a sym link for the splashscreen image so you can change it more easily afterwards, but warns against pointing the link to the boot partition.  I am now even more confused; I don't get the concept of the symlink or what to do if my /boot is on a separate partition.  Also here is a nearly entire post quoted(sorry) but I need to get clarity:

for boot splashscreen: 
"1. Adding an image
First, move the image to the grub folder (assuming the current dir is your home folder and this is were you downloaded the image).
Code:

**sudo mkdir /boot/grub/images**
**sudo mv usplash.xpm.gz /boot/grub/images**

2. Editing the Grub configuration
Backup!
Code:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

Then open the grub config file menu.lst:
Code:

**sudo gedit /boot/grub/menu.lst**

Locate a appropriate place to add the image, find the following (row 24 or therabout):
Code:

# Pretty colours
#color cyan/blue white/blue

And add a new section below the above lines:
Code:

## Splash image!
splashimage (hdX,Y)/boot/grub/images/usplash.xpm.gz

Important! You MUST replace X and Y with the proper numbers. Grub's configuration syntax is a bit weird because it does not have the same offset as the usual mount for example. X in this case is the actual disk drive and Y is the partition. Assuming you have a pretty standard installation of Ubuntu you could find this information further down in menu.lst. Locate the section which matches the entry you normally boot from:
Code:

## ## End Default Options ##
 
title		Ubuntu, kernel 2.?.??-?-??
root		(hdX,Y)

There you can find the proper numbers to use for your splashimage command.
Enter those in the line added before. Save the file.
Important2! If you have a separate boot partition you have to remove the /boot in the path, this is because the root of the boot partition is mounted in /boot on your other partition. Resulting in this section instead:
Code:

[B]  ## Splash image! (On separate partition)
splashimage (hdX,Y)/grub/images/usplash.xpm.gz[/B]

3. Seeing your results
Reboot and your splash image should be visible as the Grub background.
4. Troubleshooting
If the image somehow does not load Grub will behave weird, although if you have a timeout (Ubuntu has by default) Grub should boot Ubuntu anyway. Then you should be able to correct the problem.

Making your own splash image
Here's how you make your own image, I will not tell you how to use the Gimp as there are plenty of other tutorials on that, use google.....
...... copy it to the Grub folder:
Code:

gzip image.xpm
sudo cp image.xpm.gz /boot/grub/images

Conclusion
You should now have a nice background in Grub, and perhaps even your own creation!"    


Now when he says to remove the /boot from the path is this for every single command that refers to grub, including where to save the image?   If this is the case does that mean that I did not access my timeout change properly since I did refer to /boot/grub menu.lst  rather than /grub menu.list?  
I will have to reboot and find out soon- I hope eveything is ok.  'cause It took me forever to finally find a way to install everything in the right order so I could access all my OSs and I don't want to mess that up!  Hence the backing-up question.  Can I start by backing up just my grub for now and how does it work if it's on a separate partition!

Now I will rest my weary head.  Pls.  help is needed so greatly!

:confused:

---

### Post by goodfella on 2008-01-21
Hello,

update-grub
You do not need to use update-grub after changing your menu.lst file.  update-grub is used for automatically generating or updating a menu.lst file based on the linux kernels installed on your system.  Check the man pages for update-grub to get a better explanation.  I changed my timeout value and did not use update-grub and my GRUB menu list during boot reflected the changes I made.

GRUB images
As far as removing the /boot part from the path to the file, if in your boot partition you have a boot folder where grub resides then don't remove it.  Like for instance when I cd into my boot partition and type ls I get the following output:

boot lost+found

this is because I have a boot folder in my boot partition.  This of course is kind of redundant and probably stupid on my part but it is how I set it up about a year ago and I have not had alot of time to correct it.  So when setting the path to my splash image I have (hd0,2)/boot/grub/splash.xpm.gz.  Of course your numbers may be different.  Hope this helps if you have any other questions post them to this thread and I will try to answer them.

---

### Post by streamsanddragonflies on 2008-01-23
Hello Goodfella!
Yes, grub is in the /boot file in the /boot partition I marked during the installation, but there is also a /boot file in the / partition as well, so could there still be a conflict!?
I had installed grub on the 1st partition; sda1 (since I have 1 SCSI drive; all drives are sd, and the grub should be on sd (0,0) since it starts count at zero..  
I reread some doc and howto files and for some reason, I can't figure out how to cp or mv my splash image to boot/grub/ ( I am testing first on my old computer in Xubuntu, the terminal and files should work the same way!?)!

It says dir doesn't exist, what could I be doing wrong, noooooby me!  The image is in my home/user/bobmarleyimage(folder)/ bobmarleyimage.xpm.gz 
I downloaded some splashimages when trying the steps in the grub doc file that claimed update-grub would automatically set/find the path for the image, but this didn't work either, so I tried to create another image folder for grub to keep my image separate and easier to find/change later:

"sudo mkdir /boot/grub/onesplashimage"

then move my image to it...

 "sudo mv bobmarleyimage.xpm.gz /boot/grub/onesplashimage"

but terminal gave the following message :

"mv: cannot stat `bobmarleyimage.xpm.gz': No such file or directory"

Note:
I also had tried backing up the /boot/grub/menu.lst to a folder I created in /home or cp -r /boot to home/temp, but I got the same error message!  The only way I managed to bkup was to:
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old.

So I would like to understand how the heck to mv and cp properly as a first step, 
HELP!  :(

---

### Post by goodfella on 2008-01-24
Having both a separate boot partition and a boot folder under / is not a big deal.  However you have to note that every time you update your kernel through the automatic updates ubuntu will update the menu.lst under /boot and not under your different boot partition on sda1.

As far as the error you are receiving you need to make sure the file you are copying or moving actually exists.  Make sure that the file exists in the directory you are currently in.  You can use ls to find out what is in the current directory.  You can also use cd to change directories.  I hope this helps.  Maybe you can include the output of ls for the directory you are trying to move the file from in your next post if you are still having problems.

---

### Post by streamsanddragonflies on 2008-02-01
Hi!
Thanks Goodfella!
I think I've gotten the hang of mv and cp finally!  I'll proceed to figuring out the best steps for backing up (like my whole /home (desktop configurations and apps.) ect...) next time.  I practiced all day!  Looks like at one point I was trying to move a soft link of a file rather than the file itself and that doesn't work.  I got to copy/move around the files from two different folders in ~ to grub and even within grub itself and I got consistancy finally.  For the future,as you said, I have to make sure I cd properly to the source folder first and then I can just name the file itself rather than list the absolute path (I make less mistakes that way;it's tricky 'cause if you forget or add one thing wrong it won't work).  Yep! It shows that I'm green!  

Now in Xubuntu (Xfce) here's one annoyance that I couldn't fix when using the terminal: no matter how I try to adjust the appearance and colours in it's preferences, I have the desktop as the background interfering with properly viewing the items in the terminal screen.  No matter what I tried the screen remains relativley transparent and trying a white background bleeches out the items due to it combining with the desktop image.  At least I have a nicer terminal in my Gnome desktop...I will try to find the right info/ help but in case you know something....
After which  I can mark this one SOLVED!


Note:  I almost forgot, about the automatic updates to update the grub menu in the /boot partition:  I reread that partitions don't matter in linux like they do in windows as directories can span over many partitions if needed.  When looking at the properties of my /boot/grub folders in Ubuntu studio, it seems to have detected the right partition so it is my assumption that the right list gets automatically updated.  But if I ever have to update-grub myself, perhaps then I have to do something particularto update the right list of that partition? 


:popcorn:

---

### Post by goodfella on 2008-02-02
One thing that helps navigate directories in a terminal is using tab completion.  Tab completion works as follows:  say you are currently in your home directory and want to cd into a directory under your home directory called supercala-fristic-expialidocious.  Instead of typing
```
cd supercala-fristic-expialidocious
```
You could type cd and the first few letters of the directory name and press the tab key.  As long as the letters you typed in uniquely identify the directory you wish to go to the terminal will finish the directory name and you can press enter to go to the directory.

As far as your terminal background is concerned you may want to look into the transparency settings.  I don't know where they would be in xfce but in Gnome they are in Edit->Current Profile->Effects.

---

### Post by streamsanddragonflies on 2008-02-03
Hi Again!

Thanks for the tab trick, it's always nice to save some time! 

 By the way doing:

cd .. 

goes back 1 directory, is there a command to go forward 1 dir?

As far as Xubuntu terminal, I had tried playing around with the transparency in pref. and there must be a bug, because no matter what options or settings I did, it still would not give me an opaque screen exept if I created a white background image myself but this washed out all the text in terminal! 

 Furthuremore, there is even a washed out effect when opening up the varying preference dialog boxes as well!  I can't choose 'background colour' as an option wereas this works fine in Ubuntu Studio, which has a nicer terminal configuration. 

About my question on automatic updates and grub, it's confirmed that changes get updated in the right partition ?

After your next reply, I'll mark this thread as solved, as is overdue!
Take care! 

:KS

---

### Post by goodfella on 2008-02-04
As far as I know there is no command that goes ahead one directory, and I don't think there is because it would be hard to go ahead one directory when there are multiple directories to choose from.

As far as updating grub, as long as /boot is the mount point for your separate grub partition then the right partition will get updated.  You can check this by running the following command in a terminal:
```

mount

```

If your grub partition shows mounted on /boot then you should be in good shape.  If you are not too sure post your fstab file to this thread and I will check it for you.

---

