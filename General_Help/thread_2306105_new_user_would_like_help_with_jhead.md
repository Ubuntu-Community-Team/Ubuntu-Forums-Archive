---
title: "new user would like help with jhead"
date: 2015-12-12
forum: General Help
---

### Post by smokeyone2 on 2015-12-12
Hello

As a new user to Ubuntu I am hoping for some guidance on trying out jhead - however maybe I should mention I am completely new to using the terminal.
Just to say that my Ubuntu is on a thinkpad laptop - after waiting almost two hours trying to do a clean windows install followed by a message saying that
the system 32 file was missng I went straight over to Ubuntu from a usb install - all seems fine with the laptop -
I need to name images folders with the date and time plus maybe a short word and jhead seemed perfect -
I downloaded jhead and the software centre says installed - I then typed apt-get install jhead in the terminal but the respose was

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu-ThinkPad-X200s:~$ 

Many thanks

---

### Post by steeldriver on 2015-12-12
Hello and welcome to the forums

You seem to be mixing up different installation methods

Unlike Windows, the usual method to install software on Linux is **not** by downloading install files directly from the internet, but from distribution-specific repositories

You access those repositories either via the Software Center application, via an alternate package manager like 'synaptic', **or** from the command line via apt-get. If the Software Center says it's already installed then you don't need to also run apt-get.

The specific error you are getting is because installation of software requires administrator privileges: when you install via apt-get that means using 'sudo' - but you don't need to worry about that right now.

---

### Post by smokeyone2 on 2015-12-12
Thank you for your advice - please could you tell me where I go next -

---

### Post by steeldriver on 2015-12-12
Well it's a command-line program, so assuming it installed correctly you run it from a terminal simply by typing jhead followed by whatever options and files 

I'm not familiar with the program so I can't help you with usage - sorry - you may find the  manual page helpful

```

man jhead

```

---

### Post by smokeyone2 on 2015-12-12
Thanks again, at least now I have a clue how jhead might work -

---

### Post by smokeyone2 on 2015-12-13
Another forum member kindly pointed me in the right direction for using the command line in the terminal but I am still having problems - have search google and various websites suggest the code to use for editing Exif data - this is what happens - is there something with pictures 021.jpg I am doing wrong


ubuntu@ubuntu-ThinkPad-X200s:~$ jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' pictures 021.jpg

Error : No such file
in file 'pictures'

---

### Post by QIII on 2015-12-13
Threads merged.

You were being helped here.  Please don't start multiple threads regarding the same issue.  It causes confusion both for you and for those who would like to help.

Thanks.

---

### Post by dragonfly41 on 2015-12-13
You can try exiftool

[http://tuxdiary.com/2013/01/06/read-image-exif-data-on-ubuntu/](http://tuxdiary.com/2013/01/06/read-image-exif-data-on-ubuntu/)

---

### Post by steeldriver on 2015-12-13
> ```

ubuntu@ubuntu-ThinkPad-X200s:~$ jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' pictures 021.jpg

```

What is the name of the file whose data you are trying to modify? if it contains spaces (or other 'special' characters) then you will need to quote same as for the comment you are trying to add e.g.

```

jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' [COLOR=#0000ff]**'**[/COLOR]pictures 021.jpg[COLOR=#0000ff]**'**[/COLOR]

```
or use a backslash 'escape'
```

jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' pictures[COLOR=#0000ff]**\ **[/COLOR]021.jpg

```

OTOH if **021.jpg** is a file within a *folder* called **pictures**, you would need

```

jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' pictures[COLOR=#0000ff]**/**[/COLOR]021.jpg

```

---

### Post by smokeyone2 on 2015-12-13
Thank you for all your help - unfortuneatley I am still getting errors messages
ubuntu@ubuntu-ThinkPad-X200s:~$ jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' 'pictures 021.jpg'

Error : No such file
in file 'pictures 021.jpg'
ubuntu@ubuntu-ThinkPad-X200s:~$ jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' pictures/021.jpg

Error : No such file
in file 'pictures/021.jpg'
ubuntu@ubuntu-ThinkPad-X200s:~$

---

### Post by dragonfly41 on 2015-12-13
I have tried both jhead and exif tool and they work for me.

First change directory to the location of 'picture 01.jpg'

Here is an example

**cd ~/photogallery/img**

Now run command **ls** and check that you see 'picture 01.jpg' in the list.

In fact it would be helpful if you post to this thread the output from **ls**.

Then .. if that is the correct file name .. you can run ...

**jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' 'picture 01.jpg'**

followed by** exiftool 'picture 01.jpg'** to check metadata.

The important point is to run the terminal commands within your pictures folder.

---

### Post by smokeyone2 on 2015-12-14
Thank you for tryng to assist - amongst other points raised I had not appreciated that the terminal commands should be within my pictures folder - please could you tell me the correct way to do this - I have been opening the folder by clicking the files logo top left of screen then clicking pictures followed by Ctrl Alt T -

---

### Post by dragonfly41 on 2015-12-14
It will help you in understanding if you read through a tutorial on terminal usage and command line usage.
When you invoke "Ctrl+Alt+T" this launches a terminal window which (in your setup) looks like
this ...

ubuntu@ubuntu-ThinkPad-X200s:~$

This starting point is the user's (ubuntu) home directory.
You can then "change directory" by using command cd followed by path to your folder/directory.

Now another way is to use Nautilus to navigate to your pictures folder.
Hopefully you will see a list of photographs.

Picture 01.jpg
Picture 02.jpg
...

Now if your naming system has spaces in the file names, in any command you will need to wrap the name(s) in quotes.  That is why it is safer not to use spaces in file names (as discussed earlier).

Having arrived at your picture(s) in Nautilus, right click (context menu) and choose  "Open Terminal Here".

This launches a new terminal window 

ubuntu@ubuntu-ThinkPad-X200s:~/<path-to-your_picture>$

From there you can apply your commands.

You might find it useful to install Krusader for file navigation. Then after navigating to your folder go to Tools in toolbar menu and choose "Start Terminal Here".
However Krusader is my personal choice and Nautilus works just as well as a file manager.

==========================================================

[Post script]

On reading through your post again when you refer to "files logo" I guess that you are launching Pictures folder in **Nemo** (similar to Nautilus). Nemo also has a context menu which you can find by right clicking on your image and "Open in Terminal".

Now since you refer to Pictures folder I'm guessing that you don't have files "picture 01.jpg" and all previous discussion on this is not relevant.

But to be clear .. when you arrive at Pictures folder .. and right click on "Open in Terminal"

ubuntu@ubuntu-ThinkPad-X200s:~/Pictures$

just type the command .. **ls**

**ubuntu@ubuntu-ThinkPad-X200s:~/Pictures$ ls**

and post results here.

---

### Post by smokeyone2 on 2015-12-14
Thanks again for all your help - I'll follow your guidelines and report back - however after looking into command lines and - Having arrived at your picture(s) in Nautilus, right click (context menu) and choose  "Open Terminal Here". - I do not get this - I only get after right clicking -
New Folder
New Document
Restore missing files
Paste (not highlighted)
Properties

In the meantime I'll install Krusader for file navigation -

---

### Post by dragonfly41 on 2015-12-14
Right click on your image (01.jpg) and not the folder (Pictures).

---

### Post by smokeyone2 on 2015-12-14
Right click on your image (01.jpg) lists open with image viewer to properties - no mention of terminal -
Installed Krusader - click icon - Krusader panel opens - scroll to pictures - right click - open with - and then terminal
- error message - error executing konsole -workdir %d.

---

### Post by dragonfly41 on 2015-12-14
[COLOR=#000000]Krusader panel opens - scroll to Pictures .. then go to Tools (in top bar) and "Start Terminal Here"
or you can just press F2 instead.[/COLOR]

---

### Post by dragonfly41 on 2015-12-14
Let's make it easier and try this sequence of commands in command terminal (bypassing Nautilus, Nemo or Krusader)

```
cd ~/Pictures &&
jhead -mkexif -cl 'Your Comment Goes Here - and Keep the Single Quotes!' 01.jpg  &&
exiftool 01.jpg

```

---

### Post by smokeyone2 on 2015-12-15
Thanks for your patience - am I jinxed -

Error :  No such file

---

### Post by dragonfly41 on 2015-12-15
[1] What is the [COLOR=#b22222]*_exact_*[/COLOR] path and name of the file you are targetting?
      You can get this information from your Files manager (Nemo, Nautilus or Krusader) 
      or by navigating to your Pictures folder, right clicking on the file, Properties, and copy Name: field.
      We need to know .. is it ..
      01.jpg             (this is what I would expect)
      Pictures 01.jpg
      pictures 01.jpg

      or some other file name .. to avoid any more guessing. 

[2] I'm assuming the target file it is in your user home directory .. /home/ubuntu/Pictures
      .. otherwise defined in command line as ~/Pictures

[3] Open command terminal (Ctrl+Alt+T) and run this command
      cd ~/Pictures && ls

[4] Paste results to this forum




Command lines demand *precision *in the file path and name (even to the point of differentiating uppercase or lower case letters in paths/names).

---

### Post by smokeyone2 on 2015-12-16
There is just the solitary image in the pictures folder (testing purposes) named  01.JPG it is not inside a folder and is in the user home directory.

Ubuntu@ubuntu-ThinkPad-X200s:~$ cd ~/Pictures && ls
01.JPG  
ubuntu@ubuntu-ThinkPad-X200s:~/Pictures$ 

Success with a command line at last -

---

### Post by dragonfly41 on 2015-12-16
Remember the point I made earlier about command line [I]precision?

[/I]Look at the extension .. it is uppercase (.JPG) and not lowercase (.jpg).
In fact if you had two files 01.JPG and 01.jpg inside ~/Pictures they would be treated as two different files (but this is *_not_* recommended).
I suggest following a general rule of using lowercase extensions.
Or you can change the command line to reflect the filename (and extension).

Actually 01.JPG _*is*_ inside a folder .. /home/ubuntu/Pictures/

Your user home directory is .. /home/ubuntu/

You should be "good to go" now having picked up experience on file paths, names and syntax consistency.
But read more about command line scripting.

---

### Post by smokeyone2 on 2015-12-16
Thank you very much again for your help. I checked and looked at the name several times and still could not see the difference  but do now of course -
My generic numbering of the file had inserted uppercase JPG whereas I normally write lowercase -
Will start over on another test with a batch of images this time and watch out for upper/lower case.
Many thanks 0

---

