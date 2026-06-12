---
title: "Ubuntu 12.04.1 can't login to administrator profile"
date: 2013-08-14
forum: General Help
---

### Post by Derelinquat fenestras on 2013-08-14
Hello,

I'm in dire need of some advice!
Was using my computer as usual last night.... Installed some software--kdenlive, openshot, and related dependencies--but no major system changes...

Then I restarted my computer and I believe that the login manager is broken.
I can not login to my administrator profile... I put my password in and the screen goes blank and there are 2 lines of text, but it is not up long enough to read, and then returns me to the login manager.

I rebooted and opened in recovery mode, ran dpkg to fix broken packages, which there were a handful of, but again nothing major, all related to kdenlive.

I was worried that it was a big problem with ther kernel or something else drastic, but I am able to login to a guest session, so I feel like it is just a problem with the login manager.

I'm using ubuntu 12.04.1

Any help would be greatly appreciated!
Thank you!

---

### Post by steeldriver on 2013-08-14
Try logging in at one of the non-GUI virtual terminals (Ctrl-Alt-F1) - this will narrow down whether it is actually a login problem or just a GUI session startup problem

---

### Post by Derelinquat fenestras on 2013-08-14
I will try this...
Where do I press (Ctrl+Alt+F1)? 
at the login screen??

---

### Post by steeldriver on 2013-08-14
anytime, anywhere ... 

and Ctrl-Alt-F7 should get you back to the GUI screen when you're done

---

### Post by Derelinquat fenestras on 2013-08-14
Got it!  Thanks!

Tried to login to my main administration profile and it printed the following output:

-bash: /home/USER/.profile: line 15: syntax error near unexpected token `fi'
-bash: /home/USER/.profile: line 15: `    fi'

There are 4 spaces between ` and fi...
Should I delete 4 spaces in the .profile?

---

### Post by Derelinquat fenestras on 2013-08-14
I was able to create a 2cnd administration profile, and from it I am able to edit the .profile of my other default admin.

Would copying the contents of the .profile of the 2cd profile into the .profile of the first correct the error or are they specific for the profile being used?

---

### Post by Derelinquat fenestras on 2013-08-14
Success!!  Thank you so much for your help...

Copied and pasted the differences between the 2 .profile files and fixed the problem right away!

Can you tell me anything about what exactly the .profile does?
I was trying to install a preset for imagemagick and one of the steps for its use was altering the .profile file, and the preset didn't work and then I couldn't login...

Thanks again!

---

### Post by steeldriver on 2013-08-14
Glad you fixed it! The .profile file sets up some environment things for the login shell, a 'clean' one gets copied from /etc/skel when a new regular user account is created by the GUI or the adduser command

If you want to have another go at adding the bits for imagemagick the post back with the instructions you are following and we can try to figure out what went wrong

---

### Post by Derelinquat fenestras on 2013-08-14
Thanks for the help.

Here are the instructions posted on Fred's ImageMagick Scripts Website ([http://www.fmwconcepts.com/imagemagick/index.php](http://www.fmwconcepts.com/imagemagick/index.php)):

 > 
[LIST]
[*]These scripts are bash unix shell scripts and should work on Linux and Mac OSX with IM 6.3.5.0 or higher.

Pointers for use:
[LIST=1]
[*]Download the script
[*]Change the name to add or remove the .sh as desired when running
[*]Set the script to executable (chmod u+x)
[*]Find the full path to where IM (convert) resides by typing in a shell terminal window: type -a convert
[*]If type -a convert returns more than one path, type in a shell terminal window: path2/convert -version, where path2 is each of the paths found. Decide which version of IM you want to use.
[*]Modify your PATH environment variable so that it includes the full path to where IM (convert) resides (often /usr/bin or /usr/local/bin). This can be done by editing your .profile file. 
Alternately, edit the script somewhere between the comments and the first use of any IM command, such as just below the defaults section to add the following two lines:
imdir="path2"	#(such as imdir="/usr/local/bin" or imdir="/usr/bin")
PATH="${imdir}:${PATH}"
[*]Open a shell terminal window
[*]bash /fullpathto/scriptname(.sh) arguments /fullpathto/inputimage /fullpathto/outputimage
[*]To avoid the bash and just use scriptname(.sh) ... set your PATH to contain the location of the script
[*]Optionally edit the script to change the default directory (found after the defaults section) from dir="." to dir="/tmp"
[/LIST]
[/LIST]


---

### Post by steeldriver on 2013-08-14
well unless you have installed imagemagick by hand the binaries should already be on your PATH, e.g.

```

$ which convert
/usr/bin/convert

```

so the script(s) you downloaded should be able to find them without modifying anything

---

### Post by Derelinquat fenestras on 2013-08-14
Right, and I made it executable and moved it into /usr/bin, but I have to type out the full path to use it and
I can't seem to get it to make use of the functionality of ImageMagick (ie edit more than one photo at a time).

---

