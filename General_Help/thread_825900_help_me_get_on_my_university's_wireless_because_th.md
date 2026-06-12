---
title: "help me get on my university's wireless because they won't :("
date: 2008-06-11
forum: General Help
---

### Post by karasuman on 2008-06-11
I just started as a student at the University of Missouri - St. Louis, and they have a campus wireless network that I'd just love to be able to use with my laptop in all it's hardy glory.  Unfortunately, using their network requires authentication as described here: [https://portal.umsl.edu/authentication/](https://portal.umsl.edu/authentication/)

That involves downloading and running a program that downloads as Bradford_Dissolvable_Agent.sh (and not .exe, for some reason).  I've tried everything I can think of to get that program to do something, but nothing works.  Wine doesn't do me any good, and even trying to run it in a terminal to SEE what it's doing accomplishes nothing.

Here's the best part.  When I called campus tech support to ask for help, here's how the conversation went.

**Me**:  Hi.  I'm trying to get on your wireless network, but I can't seem to run the authentication pro--
**Tech Support**:  Windows runs it automatically.
**Me**:  I'm not running Windows.  I'm running--
**TS**:  You're not running Windows?
**Me**:  No, I'm running--
**TS**:  What are you running?
**Me**:  Ubuntu.
**TS**:  *What?!*  (At this point, he sounds highly offended, like I just called his mother an ubuntu, and he isn't sure what that is, but he doesn't like it.)
**Me**:  Linux.
**TS**:  Oh.  (You can hear the sneer.)  We don't support that.
**Me**:  You don't support that?
**TS**:  We only support Windows.
**Me**:  What if I had a Mac?
**TS**:  We support Macs.
**Me**:  Macs don't run Windows.
**TS**:  Look, if you're smart (only he says "smart" like he means "stupid") enough to get Linux (sneer) running on your computer in the first place, you should be able to figure out how to use it without needing technical support.
**Me**:  Okay.  Well, obviously, I'm not that smart, and the hoops I need to jump through to use your wireless aren't even trying to be accessible to someone not using Microsoft.
**TS**:  You made the decision to use Linux instead of Windows.  If you wanted things to work right, you would have stuck with Windows.  You're just going to have to deal with it.
**Me**:  ...wow.  Okay.  Thanks.  You have a great day.
**TS**:  (click)

---

### Post by Golem XIV on 2008-06-11
*.sh files are usually shell scripts - short programs written in the shell's command language.

Assuming this is a valid Linux shell script, right - click on the file, select "Properties", select the "Permissions" tab and enable the "Allow executing the file as a program" box.

Now open a terminal window (Applications -> Accesories -> Terminal) and run the script:
```
~/Desktop/Bradford_Dissolvable_Agent.sh
```
assuming the file was saved to your desktop (hence the ~/Desktop)
If my assumptions were correct, this should do it :-)

<edit> BTW, very snotty behaviour for a tech support person.  If he/she can't handle user requests with a minimum of civility, he/she should not be doing that job.  I'd report him/her to his/her superior.</edit>

---

### Post by karasuman on 2008-06-11
I'm mostly positive that this ISN'T a valid Linux shell script.  It's intended to run on Windows.

---

### Post by Golem XIV on 2008-06-11
I don't think Windows would know what to do with a *.sh file.  Script files for Windows have a *.bat extension.

Can you open the file in a text editor, like Gedit?  If it is a text file and it starts with something similar to **#!/bin/bash** then it most certainly is a Linux shell script file.

---

### Post by Niels Olson on 2008-06-11
If it's a shell script, it should be human-readable and we may be able to translate it for you. I can't access your link because the network won't let me past the sign in page (incidentally, LDAP SSO). Can you post the contents of the file, or attach it to a message?

FWIW, here's the company's page with some details about what they do:
[http://www.secureaccesscentral.com/nac/nac%20profiles/nac_profile_bradford.php](http://www.secureaccesscentral.com/nac/nac%20profiles/nac_profile_bradford.php)

And contact information
[http://www.secureaccesscentral.com/breakaway/contact.php](http://www.secureaccesscentral.com/breakaway/contact.php)

. Regardless of how you get this fixed, you should let them know ubuntu users want access to the network.

---

### Post by avtolle on 2008-06-11
This may be no assistance, but I googled the name of the shell script, and scanned two white papers found, which indicate this software is alleged to support Windows, Mac and Linux. So, FWIW, give Golem XIV's idea a try.

I agree this was inappropriate for the IT person (the attitude), but our younger daughter ran into a similar thing on her campus; the difference was she was able to find someone around who was a bit of a Linux person who gave her help. This may be what you're going to need to do.

---

### Post by karasuman on 2008-06-11
I appreciate the help.  :)  I don't live on campus, so I can't try this stuff out right away, but I'll see what I can do tomorrow and report back.

I really appreciate the replies!

---

### Post by karasuman on 2008-06-13
Well, still no luck.  Here's what happened when I did what GolemXIV suggested:

> beth@dell-desktop:~$ ~/Desktop/Bradford_Dissolvable_Agent.sh
awk: cmd. line:1: fatal: cannot open file `/home/beth//home/beth/Desktop/Bradford_Dissolvable_Agent.sh' for reading (No such file or directory)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 12: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 19: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 26: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 30: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 34: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 38: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 47: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory


It then launched a page in Firefox that it couldn't load because it couldn't find the file it wanted to open.

I tried opening the program as a text document, but I get a "gedit has not been able to detect the character encoding" error.

---

### Post by Golem XIV on 2008-06-13
I think we're on good ground.  The line
```
awk: cmd. line:1: fatal: cannot open file `/home/beth//home/beth/Desktop/Bradford_Dissolvable_Agent.sh' for reading (No such file or directory)
```
suggests that this IS a Linux script and that for some reason it is appending the home path twice to the file name (note the doubling of /home/beth and the double slash between them)
The rest of the errors stem from this:  The script can't file the file specified (because the path is wrong) so it can't extract the contents from the embedded gzip file.

Try copying the file on your desktop (looks like it wants to be there) and double-clicking it to run.

If it won't work, please type
```
cat Bradford_Dissolvable_Agent.sh | less
```
copy the first few lines and paste them here.  You can press **q** to exit the **less** listing.

Hopefully someone with more knowledge of awk and the command line can give you a better answer.

---

### Post by karasuman on 2008-06-13
The file is already saved to my desktop, and running it (after enabling it to BE run) just gives exactly what happened before.

When I do what you just asked me to, I get a screen filled with tildes (one per line), and hitting q gives me:

> cat: Bradford_Dissolvable_Agent.sh: No such file or directory


If I run ```
cat: /home/beth/Desktop/Bradford_Dissolvable_Agent.sh
```, I get

> #!/bin/sh
init_dir=`pwd`
mkdir .CSA.TEMP >/dev/null
\cd .CSA.TEMP
SKIP=`awk '/^__BEGIN_GZIP__/ { print NR +1; exit 0; }' $init_dir/$0`
tail -n +$SKIP $init_dir/$0 | gzip -dc | tar x
chmod +x ./engine

#LD_LIBRARY_PATH=.bncsa_deps:$LD_LIBRARY_PATH ./engine >/dev/null
#rm -r .bncsa_deps/
./engine >/dev/null
function doMoz
{
if mozilla -remote 'ping()';
then mozilla -remote "openFile(`pwd`/results.html)";
else mozilla file://`pwd`/results.html ;
fi;
}
function doNetscape
{
if netscape -remote 'ping()';
then netscape -remote "openFile(`pwd`/results.html)";
else netscape file://`pwd`/results.html;
:


---

### Post by wootah on 2008-06-13
Does she need the build-essential package?

EDIT: Nm, that was a silly question :)

---

### Post by wootah on 2008-06-13
Change the following lines:

#!/bin/sh
init_dir=`pwd`
mkdir .CSA.TEMP >/dev/null
\cd .CSA.TEMP
** SKIP=`awk '/^__BEGIN_GZIP__/ { print NR +1; exit 0; }' $init_dir`**
** tail -n +$SKIP $init_dir | gzip -dc | tar x**
chmod +x ./engine

#LD_LIBRARY_PATH=.bncsa_deps:$LD_LIBRARY_PATH ./engine >/dev/null
#rm -r .bncsa_deps/
./engine >/dev/null
function doMoz
{
if mozilla -remote 'ping()';
then mozilla -remote "openFile(`pwd`/results.html)";
else mozilla file://`pwd`/results.html ;
fi;
}
function doNetscape
{
if netscape -remote 'ping()';
then netscape -remote "openFile(`pwd`/results.html)";
else netscape file://`pwd`/results.html;

---

### Post by karasuman on 2008-06-13
change it...how?

---

### Post by wootah on 2008-06-13
> **karasuman said:**
> change it...how?

Whoops, I'm sorry.

In the console:

```

cd ~/Desktop
nano Bradford_Dissolvable_Agent.sh 

```Scroll to the lines posted above and make the changes (basically removing the /$0). Save the file with CTRL-O. Exit nano with CTRL-X.

EDIT: I hope that works. Also, please make a backup! Before you edit the file, type:
```

cp Bradford_Dissolvable_Agent.sh Bradford_Dissolvable_Agent.sh.backup

```

---

### Post by bapoumba on 2008-06-13
I cannot help you with the shell script at all, but I ran once into a problem where MacOSX was also supported (for my FAI router). I followed the procedure for Mac (adapted it to Ubuntu) and it worked. Can you have informations about the procedure for Mac ?

---

### Post by karasuman on 2008-06-13
Now, when I run it, I get this error (plus the attempt by Firefox to open a file it can't find, "Firefox can't find the file at /home/beth/.CSA.TEMP/results.html.")

> beth@dell-desktop:~$ /home/beth/Desktop/Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
awk: cmd. line:1: fatal: cannot open file `/home/beth' for reading (Invalid argument)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 12: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 19: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 26: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 30: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 34: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 38: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 47: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory


---

### Post by avtolle on 2008-06-13
WHOA! First; look at how she entered the file name, that is no space between the path name and the file name. Please renter as follows:```
/home/beth/Desktop Bradford_Dissolvable_Agent.sh
``` and see if that works.

---

### Post by karasuman on 2008-06-13
> **avtolle said:**
> WHOA! First; look at how she entered the file name, that is no space between the path name and the file name. Please renter as follows:```
/home/beth/Desktop Bradford_Dissolvable_Agent.sh
``` and see if that works.

Well, okay.  Here's what I get:

```
beth@dell-desktop:~$ /home/beth/Desktop Bradford_Dissolvable_Agent.sh
bash: /home/beth/Desktop: is a directory

```

I'm confused now.  Am I not supposed to use slashes to separate location from file name, like in Windows?  Wha...what's going on?  *hides*

---

### Post by avtolle on 2008-06-13
Beth: Try this```
cd Desktop
``` then ```
Bradford_Dissolvable_Agent.sh
``` at the prompt.

---

### Post by karasuman on 2008-06-13
Here's what I get. :-/

```
beth@dell-desktop:~$ cd Desktop
beth@dell-desktop:~/Desktop$ Bradford_Dissolvable_Agent.sh
bash: Bradford_Dissolvable_Agent.sh: command not found

```

---

### Post by wootah on 2008-06-13
> **karasuman said:**
> Here's what I get. :-/

```
beth@dell-desktop:~$ cd Desktop
beth@dell-desktop:~/Desktop$ Bradford_Dissolvable_Agent.sh
bash: Bradford_Dissolvable_Agent.sh: command not found

```


Ohhhhhhhhh, I see what happened way above! I apologize karasuman, I didn't read your original post carefully. Do you have that backup? If so, type in the following:

```

cd ~/Desktop
mv Bradford_Dissolvable_Agent.sh.backup Bradford_Dissolvable_Agent.sh
./Bradford_Dissolvable_Agent.sh

```

When you first called it with ~/Desktop/Bradford_Dissolvable_Agent.sh, bash expanded the ~ into /home/beth which caused a problem in the script since the current directory you were in was already /home/beth.

---

### Post by avtolle on 2008-06-13
OK, I think my fingers got ahead of my head. Let me look at this a bit, and I'll be back (all the while hoping someone else will come up with the solution).

---

### Post by avtolle on 2008-06-13
> **wootah said:**
> Ohhhhhhhhh, I see what happened way above! I apologize karasuman, I didn't read your original post carefully. Do you have that backup? If so, type in the following:

```

cd ~/Desktop
mv Bradford_Dissolvable_Agent.sh.backup Bradford_Dissolvable_Agent.sh
./Bradford_Dissolvable_Agent.sh

```When you first called it with ~/Desktop/Bradford_Dissolvable_Agent.sh, bash expanded the ~ into /home/beth which caused a problem in the script since the current directory you were in was already /home/beth.

And my bad for flying right past the "./" part. Hope you have the backup, or can get another copy of the shell file.

---

### Post by wootah on 2008-06-13
> 
			 				beth@dell-desktop:~$ **~/Desktop/Bradford_Dissolvable_Agent.sh**
awk: cmd. line:1: fatal: cannot open file `**/home/beth//home/beth/Desktop/Bradford_Dissolvable_Agent.sh**' for reading (No such file or directory)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 12: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 19: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 25: netscape: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 26: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 30: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 34: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 38: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 47: function: not found
/home/beth/Desktop/Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory


~ expanded out into /home/beth//home/beth/Desktop/Bradford_Dissolvable_Agent.sh which is ~ + pwd :( Very subtle

---

### Post by wootah on 2008-06-13
> **avtolle said:**
> And my bad for flying right past the "./" part. Hope you have the backup, or can get another copy of the shell file.

Your post made me go back and check what she originally typed :)

---

### Post by avtolle on 2008-06-13
wootah, I'm totally unaware of how many times I've made typos like that, which is why I went looking for something like that in the first place.

Also, the expansion you caught is quite subtle, no?, as was pointed out by you, too.

---

### Post by wootah on 2008-06-13
> **avtolle said:**
> wootah, I'm totally unaware of how many times I've made typos like that, which is why I went looking for something like that in the first place.

Also, the expansion you caught is quite subtle, no?, as was pointed out by you, too.

*high-five* Working like a team! :-D

---

### Post by karasuman on 2008-06-13
Okay.  Here's my latest attempt, with several false starts in the beginning because I had to figure out how to type what you guys told me to type.  ;)  I'm learning, though, I promise.  (I put my goofiness in italics.)

```
beth@dell-desktop:~$ cd ~/Desktop
[I]beth@dell-desktop:~/Desktop$ mv Bradford_Dissolvable_Agent.sh.backup Bradford_Dissolvable_Agent.sh ./Bradford_Dissolvable_Agent.sh
mv: target `./Bradford_Dissolvable_Agent.sh' is not a directory
beth@dell-desktop:~/Desktop$ mv Bradford_Dissolvable_Agent.sh.backup Bradford_Dissolvable_Agent.sh
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
bash: ./Bradford_Dissolvable_Agent.sh: Permission denied
beth@dell-desktop:~/Desktop$ chmod +x /Bradford_Dissolvable_Agent.sh
chmod: cannot access `/Bradford_Dissolvable_Agent.sh': No such file or directory
beth@dell-desktop:~/Desktop$ chmod +x ./Bradford_Dissolvable_Agent.sh[/I]
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
./engine: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `tmp.csa': No such file or directory

```

---

### Post by avtolle on 2008-06-13
While I'm working out the first missing dependency problem, karasuman, what browser do you have installed? This is the source of the following error messages, that is, the script is trying to find your browser. You may have already told us, but short term memory for those of us shall we say looking forward (?) to our 40th high school class reunion is sometimes a bit lacking. :-)

---

### Post by karasuman on 2008-06-13
Haha.  :)  I'm using Firefox 3.0b5.

---

### Post by avtolle on 2008-06-13
OK, now, anyone else out there got the answer to this question: Will installing build-essential take care of the dependency problem (yes, I'm being lazy)?

karasuman, while awaiting the response to my question, have you already downloaded and installed all the updates to 8.04?

---

### Post by avtolle on 2008-06-13
karasuman, if you're still with me, go to the terminal and do```
sudo aptitude update && sudo aptitude install build-essential
```then try to run the shell script again. Thank you.

---

### Post by karasuman on 2008-06-13
> **avtolle said:**
> OK, now, anyone else out there got the answer to this question: Will installing build-essential take care of the dependency problem (yes, I'm being lazy)?

karasuman, while awaiting the response to my question, have you already downloaded and installed all the updates to 8.04?

Just double-checked.  I have indeed.

---

### Post by avtolle on 2008-06-13
Interesting; my updates have updated my FF to 3.0 rc1 from 3.0 Beta 5. Some repositories take a while tu update, so don't worry about this right now. I'm also having a concern about the directories the script is looking for, given the seeming new names for 3.0 whatever installation files, but again, don't worry about that right now.

---

### Post by karasuman on 2008-06-13
> **avtolle said:**
> karasuman, if you're still with me, go to the terminal and do```
sudo aptitude update && sudo aptitude install build-essential
```then try to run the shell script again. Thank you.

Just to make sure I'm on the right page, should I be running the original script or the modified version?  (I still have both saved.)

Here's what I get when I run the original:

```
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
./engine: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `tmp.csa': No such file or directory

```

I think that's at least a little different from before.  :-/

---

### Post by avtolle on 2008-06-13
If, by modified, you mean the one suggested earlier, back it up (just in case) and try running it. I'll try to hang in a bit longer, but I'm needing to leave shortly. Let's give it a go and see what happens.

FYI, if I can articulate this correctly, the error message about the missing file or directory libstdc++.so.5 is concerning me right now. But first, do as you suggested, and we'll see what happens.

---

### Post by karasuman on 2008-06-13
Okay, here's what happens when I run the one that you guys had me modify earlier:

```
beth@dell-desktop:~$ cd Desktop
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
awk: cmd. line:1: fatal: cannot open file `/home/beth/Desktop' for reading (Invalid argument)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
./Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory

```

I really appreciate all the time you (and others) are spending on this with me.  :)

---

### Post by avtolle on 2008-06-13
Looks like that one might have gotten "bit" by the expansion bug, too; but whatever.

I'm going to take another look at the "modified version" and try to get back shortly.

---

### Post by avtolle on 2008-06-13
Hopefully wootah is still around. I'm leaning more and more towards the problem being the "missing" library (libstdc++.so.5) as being (at least the first) part of the problem. So, the question becomes, where this library might be, if installed (as the script isn't finding it); or, if not installed, which package is it a part of that, when installed, might correct this error. Pondering time.

Thank you for your kind words, karasuman. It just irks me that your school is making this so difficult for you (as my daughter's school did for her).

---

### Post by avtolle on 2008-06-13
To explain my mutterings about the missing library a bit. It (the script) is, as near as I can tell, looking in your home directory for it, and isn't finding it there (or any link, etc. to another place where it might be). Parsing the script, it appears that the lib file is needed to get things started, and without that, it just stalls out without doing anything. Not much solace to you right now, but I thought I'd try to explain where my mind is at.

---

### Post by avtolle on 2008-06-13
karasuman, I've nothing more to offer at the moment, and must go now. Good luck, and hopefully, someone else will see my unsuccessful attempts, and find the "magic bullet" to get you up and running. Have a good weekend.

---

### Post by wootah on 2008-06-13
> **avtolle said:**
> To explain my mutterings about the missing library a bit. It (the script) is, as near as I can tell, looking in your home directory for it, and isn't finding it there (or any link, etc. to another place where it might be). Parsing the script, it appears that the lib file is needed to get things started, and without that, it just stalls out without doing anything. Not much solace to you right now, but I thought I'd try to explain where my mind is at.

Ack sorry guys, I got caught up while creating a new thread of importance to Canadians.

Anyways, yes it looks like you are missing some dependencies. You mentioned that you already have build-essential installed?

EDIT: This is what i get when I do the following:
```

tripp@eclipse-desktop:~$ locate libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.1/libstdc++.so
/usr/lib/libstdc++.so.6.0.9
/usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.5.0.7
/usr/lib/libstdc++.so.6

```
I have the one that is missing... do you have it?

---

### Post by karasuman on 2008-06-13
Here's what I get:

```
beth@dell-desktop:~$ locate libstdc++.so
/home/beth/maple11/bin.IBM_INTEL_LINUX/libstdc++.so.2.9
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6.0.9
beth@dell-desktop:~$ 


```

not sure why maple is coming up...at all?

---

### Post by wootah on 2008-06-13
```
sudo apt-get install libstdc++5
```Then try running the script again :)

EDIT: My favorite part of this entire script is this line:
> 
Error running CSA.sh.  Please call the helpdesk.
:lolflag:

---

### Post by karasuman on 2008-06-13
This is seriously starting to make my head spin.

I did the app-get you said:

```
beth@dell-desktop:~$ sudo apt-get install libstdc++5
[sudo] password for beth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 447kB of archives.
After this operation, 1081kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy/universe gcc-3.3-base 1:3.3.6-15ubuntu4 [151kB]
Get:2 http://archive.ubuntu.com hardy/universe libstdc++5 1:3.3.6-15ubuntu4 [296kB]
Fetched 447kB in 2s (206kB/s)      
Selecting previously deselected package gcc-3.3-base.
(Reading database ... 161954 files and directories currently installed.)
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu4_i386.deb) ...
Setting up gcc-3.3-base (1:3.3.6-15ubuntu4) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Looks like that went okay.  (At least, nothing pops out as HAHAHA, no.)

Then I tried running the script again.  This is the original script, as it was when I downloaded it.  It took forever to write more than the first line, but then it finally gave me this, along with a NEW Page Load Error in Firefox (now it says "Firefox can't find the file at /authentication/Fail.html."):

```
beth@dell-desktop:~$ cd Desktop
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
bash: ./Bradford_Dissolvable_Agent.sh: Permission denied
beth@dell-desktop:~/Desktop$ chmod +x ./Bradford_Dissolvable_Agent.sh
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
./Bradford_Dissolvable_Agent.sh: 56: doFirefox: not found
./Bradford_Dissolvable_Agent.sh: 56: doMoz: not found
./Bradford_Dissolvable_Agent.sh: 56: doNetscape: not found
./Bradford_Dissolvable_Agent.sh: 56: doOpera: not found
./Bradford_Dissolvable_Agent.sh: 56: doSeamonkey: not found
./Bradford_Dissolvable_Agent.sh: 56: doEphy: not found
./Bradford_Dissolvable_Agent.sh: 56: doKonq: not found

```

Just for kicks, I tried it with the one you guys had me modify (and Firefox gives me the following Page Load Error: "Firefox can't find the file at /home/beth/Desktop/.CSA.TEMP/results.html"):

```
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
awk: cmd. line:1: fatal: cannot open file `/home/beth/Desktop' for reading (Invalid argument)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
./Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory

```

I like the "please call the help desk" bit, too.  I figure it's like praying, only less effective.  Or you guys are the help desk, and it's like praying, but more effective.

EDIT:  hey hey hey, wait.  That first error, where Firefox can't find the authentication/fail file.  Could that be because I'm just not on campus and not connected to the network it wants to authenticate on?  I live too far away to drive up there and try this right now, but I'll definitely give that a go in the future...

---

### Post by moore.bryan on 2008-06-13
> **karasuman said:**
> EDIT:  hey hey hey, wait.  That first error, where Firefox can't find the authentication/fail file.  Could that be because I'm just not on campus and not connected to the network it wants to authenticate on?  I live too far away to drive up there and try this right now, but I'll definitely give that a go in the future...
that's **completely** possible... a question, though: are you executing the script as sudo? if not, does it make any difference when you do?

---

### Post by karasuman on 2008-06-13
> that's completely possible... a question, though: are you executing the script as sudo? if not, does it make any difference when you do?

I need a little more explanation about what you mean by that.  I know I've run some commands that started with sudo and required my password, but that's it.  :-/

---

### Post by wootah on 2008-06-13
> **karasuman said:**
> This is seriously starting to make my head spin.

I did the app-get you said:

```
beth@dell-desktop:~$ sudo apt-get install libstdc++5
[sudo] password for beth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 447kB of archives.
After this operation, 1081kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy/universe gcc-3.3-base 1:3.3.6-15ubuntu4 [151kB]
Get:2 http://archive.ubuntu.com hardy/universe libstdc++5 1:3.3.6-15ubuntu4 [296kB]
Fetched 447kB in 2s (206kB/s)      
Selecting previously deselected package gcc-3.3-base.
(Reading database ... 161954 files and directories currently installed.)
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu4_i386.deb) ...
Setting up gcc-3.3-base (1:3.3.6-15ubuntu4) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```Looks like that went okay.  (At least, nothing pops out as HAHAHA, no.)

Then I tried running the script again.  This is the original script, as it was when I downloaded it.  It took forever to write more than the first line, but then it finally gave me this, along with a NEW Page Load Error in Firefox (now it says "Firefox can't find the file at /authentication/Fail.html."):

```
beth@dell-desktop:~$ cd Desktop
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
bash: ./Bradford_Dissolvable_Agent.sh: Permission denied
beth@dell-desktop:~/Desktop$ chmod +x ./Bradford_Dissolvable_Agent.sh
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
./Bradford_Dissolvable_Agent.sh: 56: doFirefox: not found
./Bradford_Dissolvable_Agent.sh: 56: doMoz: not found
./Bradford_Dissolvable_Agent.sh: 56: doNetscape: not found
./Bradford_Dissolvable_Agent.sh: 56: doOpera: not found
./Bradford_Dissolvable_Agent.sh: 56: doSeamonkey: not found
./Bradford_Dissolvable_Agent.sh: 56: doEphy: not found
./Bradford_Dissolvable_Agent.sh: 56: doKonq: not found

```Just for kicks, I tried it with the one you guys had me modify (and Firefox gives me the following Page Load Error: "Firefox can't find the file at /home/beth/Desktop/.CSA.TEMP/results.html"):

```
beth@dell-desktop:~/Desktop$ ./Bradford_Dissolvable_Agent.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
awk: cmd. line:1: fatal: cannot open file `/home/beth/Desktop' for reading (Invalid argument)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
chmod: cannot access `./engine': No such file or directory
./Bradford_Dissolvable_Agent.sh: 11: ./engine: not found
./Bradford_Dissolvable_Agent.sh: 12: function: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 18: mozilla: not found
./Bradford_Dissolvable_Agent.sh: 19: function: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 25: netscape: not found
./Bradford_Dissolvable_Agent.sh: 26: function: not found
./Bradford_Dissolvable_Agent.sh: 30: function: not found
./Bradford_Dissolvable_Agent.sh: 33: epiphany: not found
./Bradford_Dissolvable_Agent.sh: 34: function: not found
./Bradford_Dissolvable_Agent.sh: 37: konqueror: not found
./Bradford_Dissolvable_Agent.sh: 38: function: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 46: seamonkey: not found
./Bradford_Dissolvable_Agent.sh: 47: function: not found
./Bradford_Dissolvable_Agent.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `engine': No such file or directory
rm: cannot remove `agent.config': No such file or directory
rm: cannot remove `tmp.csa': No such file or directory

```I like the "please call the help desk" bit, too.  I figure it's like praying, only less effective.  Or you guys are the help desk, and it's like praying, but more effective.

EDIT:  hey hey hey, wait.  That first error, where Firefox can't find the authentication/fail file.  Could that be because I'm just not on campus and not connected to the network it wants to authenticate on?  I live too far away to drive up there and try this right now, but I'll definitely give that a go in the future...

I think the old script (the one we had you modify) is done for. You can delete it :)

As for the rest, I think you might be right! Can you post the URL of the page it is trying to get you to go to ? Perhaps we have it solved :-D

---

### Post by moore.bryan on 2008-06-13
no worries... i meant, did you run the script this way:
```
sudo ./Bradford_Dissolvable_Agent.sh
```
also, could you post the code of the script as you have it right now? a fresh pair of eyes might help your cause.
[FONT=monospace][/FONT]

---

### Post by SlCKB0Y on 2008-06-13
> **avtolle said:**
> WHOA! First; look at how she entered the file name, that is no space between the path name and the file name. Please renter as follows:```
/home/beth/Desktop Bradford_Dissolvable_Agent.sh
``` and see if that works.

ERRR What?
](*,)

---

### Post by avtolle on 2008-06-14
karasuman, looks like you are on the right track. My apologies for not having you do the check wootah had you do for the missing library, and not having you do the sudo apt-get thing to install it; DUH. Although, I thought installing build-essential might pick it up.

Good luck when you get to campus. From scanning the white papers I mentioned "way back", the agent looks for the browser (Firefox in your case) to authenticate it for use by your computer on the network. One other thing I'll mention here, based upon my daughter's experience; at some point, this program will look for an anti-virus or virus scanning program installed on your computer which is up to date. I'm not sure what your folks will accept, but there are several you might look at to install on the Linux side. I'm rather likely getting the cart before the horse here, but if this does come up, then you'll need to install one. There's clamav from the repositories; there are also AVG for Linux and Avast! Home Free Edition for Linux, either of which need to be downloaded from the respective company's web site and installed. FYI.

---

### Post by karasuman on 2008-06-24
Well, I've been trying, and I guess it's time to give up.  Thanks to all the help you guys gave me, I did manage to get the file to run properly and announce my success.  Unfortunately, it still won't let me actually access the network.

The tech support guy at UMSL says it's either because it's falsely giving me the success message, or... he has no idea because it's linux and they don't DO linux.

Thanks for all of your help.

---

### Post by moore.bryan on 2008-06-25
sorry to see you subdued by an unhelpful tech department... logic says there must be a way for you to log-on.

---

### Post by karasuman on 2008-06-25
I'm still working on it with a friend I've made in the class I'm taking this term, but there's not much else I can reasonably ask you guys for... at least not until I have a better idea of what's not working.  I just wanted to update to let you know that I appreciated the time and effort you guys put in.  I'm just not sure what else I could ask for help with that wouldn't require someone who could at least mess around with the same network.  ;)

---

### Post by moore.bryan on 2008-06-25
good point... being there may make a difference. i wonder, though, what *exactly* the script was meant to do. if it was meant to authenticate your computer onto the network, it's possible the *secret* is in the file itself; if not, i'm not sure what it's purpose *would* be.

---

### Post by avtolle on 2008-06-25
> **moore.bryan said:**
> good point... being there may make a difference. i wonder, though, what *exactly* the script was meant to do. if it was meant to authenticate your computer onto the network, it's possible the *secret* is in the file itself; if not, i'm not sure what it's purpose *would* be.
I'll second the being there may make a difference. From discussions with my daughter, who ran into the same problem, with the same program as I understand it from talking with her, the purpose is to authenticate the computer on the campus network, check to see that there is an "approved" browser installed, and to ensure that the user has an active anti-virus program installed and running, to avoid a virus getting out into the network itself. 

karasuman, you and your friend might Google for the white papers I found when this whole thing started. One thing that sticks in my memory is that the program (Bradford Dissolving Agent) handles linux boxes differently than Windows machines and Macs. Something about staying logged in after there is "success" for additional configuration, as I recall. Good luck; and non illegitimi carborundum.

---

### Post by wootah on 2008-06-25
> **karasuman said:**
> I'm still working on it with a friend I've made in the class I'm taking this term, but there's not much else I can reasonably ask you guys for... at least not until I have a better idea of what's not working.  I just wanted to update to let you know that I appreciated the time and effort you guys put in.  I'm just not sure what else I could ask for help with that wouldn't require someone who could at least mess around with the same network.  ;)

Please let us know if there is anything else we can help you with. You piqued my curiosity ;)

---

### Post by avtolle on 2008-06-25
Wootah: Google Bradford Dissolvable Agent, and take a look at the first link that pops up. Obviously, it is directed at Loyola (not sure which one) but there are three fixes listed there. Wondering, without knowing, if anything there would be transmissible to karasuman? I direct her and her friend to the same link, to see if it makes any sense. Only if you have time, of course. :-)

For example, there is discussion of a linux box being a "gaming machine" for purposes of logging on/getting established under the checking system performed by the Agent. There is a bunch of stuff there that might make sense if I was sitting next to her, but from a distance all I can do is wonder.

---

### Post by wootah on 2008-06-25
> **avtolle said:**
> Wootah: Google Bradford Dissolvable Agent, and take a look at the first link that pops up. Obviously, it is directed at Loyola (not sure which one) but there are three fixes listed there. Wondering, without knowing, if anything there would be transmissible to karasuman? I direct her and her friend to the same link, to see if it makes any sense. Only if you have time, of course. :-)

For example, there is discussion of a linux box being a "gaming machine" for purposes of logging on/getting established under the checking system performed by the Agent. There is a bunch of stuff there that might make sense if I was sitting next to her, but from a distance all I can do is wonder.

Well I took a look around and found this: [http://wiki.luc.edu:8080/display/BRDF/Linux](http://wiki.luc.edu:8080/display/BRDF/Linux)
It seems there is another client that is required. Hopefully karasuman takes a look at this thread again. Perhaps it is just as simple as installing that client :)

IMO, this is a poor way to authenticate users on a campus network :( My university doesn't have anything near this complex and we have never had a serious network outages because of virii, malware, etc.

EDIT: Omgosh. I would **not** want to use this network. The kind of stuff these guys are tracking is unbelievable. I, personally, like my own security thank you :)

---

### Post by karasuman on 2008-06-25
So, it looks like I need (one of) those two libraries, as well as an additional client?  I'm not sure what client it means.  I'm timing out on downloading the libraries right now, but I'll try again later and see how that goes.

---

### Post by avtolle on 2008-06-25
You only need the .deb one, not the .rpm one, if that helps at all.

---

### Post by karasuman on 2008-06-26
The links in the site don't seem to be working ever.  When I google for the .deb file, I get a whole bunch of links about the .rpm one.  It looks like the .deb is for Debian-based systems, and the .rpm is for Fedora?  I tried to mess around with apt-get and stuff to find the file, but I haven't had any luck.  If I do manage to find the file, what do I do with it?

---

### Post by Taxman415a on 2008-06-26
If you get the deb, you can always just put it on the desktop and double? click on it and select install. You'll notice I never do it that way though, I open a terminal and cd to the directory the deb is in and use dpkg -i foo.deb or throw it in /var/cache/apt/archives where the package managers store debs and use aptitude to install the deb.

Incidentally have you tried calling tech support back? Sometimes it's just as easy as getting a different person that has more of a clue and is willing to be helpful. The other option is you can't be the only person on campus that has tried this, so seek out the other linux enthusiasts. There has to be some sort of mailing list or group or something on your campuse website somewhere. Actually there are probably plenty of people at your uni using linux for high performance computing projects and the silly tech support just doesn't know it because those projects just support themselves.

---

### Post by Dylnuge on 2008-06-26
Did you ever try running the command with sudo? Put sudo in the front and enter your password, it might work then.

If it still doesn't, the .exe might run under wine. Sometimes I have found that Windows programs are written more cleanly then their Linux equivilents (which are just sloppy ports sometimes), and therefore, it might run under wine. Sounds like when you went to the site, it gave you the Linux file automaticly (Windows wouldn't run a .sh nativly anymore then Linux would a .exe).

A .deb would be good too, and yes, .deb files run on Debian-based Linux systems that use apt (like Ubuntu).

Best of luck.

---

### Post by avtolle on 2008-06-28
@karasuman, if you are still with us; I've a feeling that the deb package that you cannot get may not be needed (from the link, that is), and it may already be installed. In Synaptic, search libstdc and see whether there isn't at least one of these already installed. 

Rationale: the package refers to compat-libstdc, which, as that link goes to a site of the particular university, got me thinking that perhaps, and only perhaps, there are linux users and distros being used that do not have a compatible package, i.e., one compatible with Bradford. From reading the description of the two libstdc (there's more, but in my case, both "++5" and "++6" are installed), this is a standard package. 

What the libstdc is needed for is to read your computer's MAC address and return the reading to the host system. For this purpose, the MAC address relates to your network card. I've a feeling, again just a feeling, that the appropriate library is already installed or may be installed on your system w/o the need to download the package from luc.edu. Good luck.

---

### Post by h218design on 2008-08-26
Karasuman,

I had the same problem with my university system... damn CSA.sh!

But my IT guys are cool with linux.  Here's what I had to do:

1.  If you can download the CSA.sh file, you can get onto the network, right?

2.  For us we have the option to "register a handheld device"

3.  I clicked on that, typed in my username, password, and ran "ifconfig" in terminal to get my ip address: 192.168....  (remember your looking for the "WAN0" line).

4.  I entered my ip address and hit submit.

5.  In about a sec the webpage changed to let me know that I was registered and should be good to go.

6.  I told WICD to connect to their network automatically, then rebooted.

When I came back up, I was connected and able to use their wifi network.

Hope this helps!

---

### Post by karasuman on 2008-08-26
I'm going to try this when I get to campus tomorrow.  I'm not sure how to get my IP address, though.  I ran ifconfig:

```
beth@grumpy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:53:c4:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1f:3c:58:98:4e  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe58:984e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31791065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29409371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2473462872 (2.3 GB)  TX bytes:3358607236 (3.1 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:143370 (140.0 KB)  TX bytes:143370 (140.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-58-98-4E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I don't see a line that says WAN0.  :-/

---

### Post by Unanimated on 2008-08-26
I'm positive that someone has already suggested this, but you could try this:

```
cd ~/Desktop
chmod +x Bradford_Dissolvable_Agent
./Bradford_Dissovable_Agent
```

I don't think I spelled dissolvable right, so don't copy+paste this.

---

### Post by h218design on 2008-08-28
When you're on the network registration page (using your wireless card) I believe it'll be WAN0... if you're using your ethernet port it'll be ETH0 or ETH1.  

"inet addr:192.168.1.102 " is showing on your ETH1... I'd try that.  

I hope this helps.

---

### Post by mssever on 2008-08-28
> **h218design said:**
> When you're on the network registration page (using your wireless card) I believe it'll be WAN0... if you're using your ethernet port it'll be ETH0 or ETH1.  

"inet addr:192.168.1.102 " is showing on your ETH1... I'd try that.  

I hope this helps.
It has nothing to do with the network. It has to do with the driver or card. On my old laptop with a Broadcom 4306, the wireless card was called eth1 until I manually changed it. On this machine with an Intel wireless card (don't know the model), it's called wlan0. In both cases, the wired card was called eth0.

EDIT: So I suspect that eth1 is karasuman's wireless card. The way to test this is to try ```
sudo iwlist eth1 scan
``` replacing eth1 with the device you're testing. If you get an attempt to scan, you know you have your wireless card. A non-wireless card will return ```
eth0      Interface doesn't support scanning.
```

---

### Post by Crafty Kisses on 2008-08-28
See what comes out of this:
```
lshw -C network
```
This is a Linux script, so in theory this could technically work.

---

### Post by fahadsadah on 2008-08-28
Can I just say to Golem XIV:

Why do you pipe cat into less?
Less will read from STDIN, but the preferred method of input is a file - thus no need to use cat at all.

For example: ```
cat file | less
``` is equivalent to ```
less file
```

---

### Post by Krupski on 2008-08-28
> **karasuman said:**
> I just started as a student at the University of Missouri - St. Louis, and they have a campus wireless network that I'd just love to be able to use...

My employer is a state university.

*OUR* wireless network is open (i.e. no encryption), but we enforce MAC address authentication.

It's quite possible that your university does the same thing.

If so, just call their IT department, ask to talk to a supervisor or someone who actually knows what's going on.

Ask them if they use MAC address validation and, if so, could they register YOUR MAC address?

To find out your computer's MAC address, use the 'iconfig' command in a terminal window like this:

```

sudo ifconfig

```

It will return something that looks like this:

```

eth0      Link encap:Ethernet  HWaddr **[COLOR="Blue"]00:01:02:FC:FD:FE[/COLOR]**
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          (other stuff here)
          (other stuff here)

```

The blue bolded area is the MAC address (which will be different for your computer - they are globally unique - the above is just an example).

If your school uses MAC address authentication, giving the admin your number and having it added to their database should solve your problem.

Good luck!

-- Roger

---

### Post by mssever on 2008-08-28
> **Krupski said:**
> *OUR* wireless network is open (i.e. no encryption), but we enforce MAC address authentication.
I'm glad I don't use that network! Universities are quite hostile environments, and an unencrypted network is a heyday for lowlifes who enjoy eavesdropping and other, more nefarious, activities. Furthermore, MAC filtering provides virtually no security since it's so easy to spoof a MAC address.

---

### Post by Krupski on 2008-08-29
> **mssever said:**
> I'm glad I don't use that network! Universities are quite hostile environments, and an unencrypted network is a heyday for lowlifes who enjoy eavesdropping and other, more nefarious, activities. Furthermore, MAC filtering provides virtually no security since it's so **easy to spoof a MAC address**.

Actually... I put a gigabit network card into my office computer to replace the 10/100 built in NIC. Rather than bothering to call the IT people to register the new MAC, I just spoofed the old one. It worked fine.

(they use MAC filtering for wired connections too).

-- Roger

---

### Post by jgrabham on 2008-09-13
Anyone got a way to get around this then, the College I just started uses the same system, I'm thinking of spoofing a MAC address, but then I'd need an address to spoof...

I may run Norton in WINE, the run the appropriate CSA.exe in WINE, yet another thing to try.

Any more ideas?  I have read through the last 8 pages, and I'll try what has already been suggested.

EDIT - >  Re: Bradford Networks CSA
I finally figured it all out! Just for future reference for anyone running into a similar problem, you just need to install libstd c++ v.5 and it works perfectly. You still get some errors in the console but at least it lets you register on the network. It seems that the newer versions of Ubuntu have v.6 pre-installed, but Bradford CSA needs v.5. It was actually this line that gave me the hint:

" error while loading shared libraries: libstdc++.so.5: "

I hope this proves usefull!! - [From this thread]("http://ubuntuforums.org/showthread.php?t=813265")

If it works, I'll let you know.  I'm not in to check until Tuesday though.

---

### Post by mb_webguy on 2008-09-13
> **Krupski said:**
> If your school uses MAC address authentication, giving the admin your number and having it added to their database should solve your problem.

Good luck!

-- Roger

+1

My local university also uses this method, and until recently used an ActiveX control to upload the client's MAC address to the server so it could be added to the database.  They changed to a different system because they were fielding so many calls from Mac and Linux users (and people who used Firefox and couldn't figure out why it wasn't working) asking to be added to the database.

If you call them up and explain your situation to someone other than the helpdesk jockey, they'll probably add your MAC address to the database.

---

### Post by philbee on 2008-10-02
I have a similar problem with my iPAQ 214; while it works on most WiFi networks it fails to work on my University network!  I contunually get the message "Bradford Dissolvable Agent is not a valid Pocket PC application".  Why doesn't this thing (BDA) recognise the existence of PDAs and Smartphones?

---

