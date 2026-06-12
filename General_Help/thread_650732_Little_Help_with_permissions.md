---
title: "Little Help with permissions"
date: 2007-12-26
forum: General Help
---

### Post by Dreamy1 on 2007-12-26
I am very new to the permissions thingy and I don't know what to do exactly.

See I want to extract some files into a directory in the Ubuntu Partition but I keep getting a permission denied error, I know it isn't complex but for me it is. I know I have to type something when extracting files but that alone confuses me.

To be more specific I am installing some Windows fonts and I am extracting the files as per [this tutorial]("http://ubuntuforums.org/showthread.php?t=208396") says but I have hit a roadblock with the permissions part, help would be greatly appreciated.

---

### Post by taurus on 2007-12-26
Did you follow the commands that he used in that thread, especially including the **sudo** in front?

---

### Post by Dreamy1 on 2007-12-26
Gosh that was fast.

Um this is really the part I find confusing, what is the Sudo step? I see the code there but I don't know what to do with it when I extract the files, could someone explain to me what I do, sorry, total newbie here.

---

### Post by Dreamy1 on 2007-12-26
I figured that I type the sudo text in a command line or something to that effect, is this correct?

---

### Post by taurus on 2007-12-26
First off, you have to run all those commands from a terminal so open one up with Applications -> Accessories -> Terminal.  

Now, you need to download msfonts.tbz.  Type this into the terminal.

```
cd ~/Desktop
wget -c http://www.osresources.com/files/centos-windows-fonts/msfonts.tbz
```
Then, you need to exact and install it with

```
sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/
```
When it asks for a password, use the same password that you are logged in with.

Otherwise, open synaptic, System -> Administration -> Synaptic Package Manager, and Search for **msttcorefonts** and install it from there.

---

### Post by Dreamy1 on 2007-12-26
Well I did it, I think I succeeded it, it asked me for the password and then all the list of files appeared in a scrolling form, so I assume I did it correctly. Thankyou so much for the help! :) 

Edit: I can now see the Windows fonts now.

---

### Post by taurus on 2007-12-26
If you want to be sure, you can list those files from a terminal with

```
ls -la /usr/share/fonts/truetype
```

---

### Post by Dreamy1 on 2007-12-26
> **taurus said:**
> If you want to be sure, you can list those files from a terminal with

```
ls -la /usr/share/fonts/truetype
```

Ok I did that and this is what it came up with...

[http://img244.imageshack.us/img244/6873/screenshotstevenubuntuujh9.png](http://img244.imageshack.us/img244/6873/screenshotstevenubuntuujh9.png)

---

### Post by taurus on 2007-12-26
Those are the fonts that you've just installed.  Looks like everything is running fine your end now with windows fonts.

---

### Post by Dreamy1 on 2007-12-26
> **taurus said:**
> Those are the fonts that you've just installed.  Looks like everything is running fine your end now with windows fonts.

Well it looks like my problem is solved. Thanks for the help. :)

---

### Post by Dreamy1 on 2007-12-26
Sorry to bring this up again, but anyway I have a copy of XAMPP personal web development server sitting on my desktop and I have trouble figuring out what to type in sudo to get it to install, the file is already extracted and is sitting on my desktop waiting to be installed, except on the tutorial it says that I should put the file in the "/opt" folder, but I can't do that because of the permissions.

I know now about the sudo thingy but you could you give me some sort of command code?
Additionally the folder is called "lampp" on my desktop.

---

### Post by taurus on 2007-12-26
You can try something like

```
sudo cp -R ~/Desktop/lampp /opt
```

Or you can run

```
gksudo nautilus
```
and just drag whatever directory you want to /opt to move it.

---

### Post by Dreamy1 on 2007-12-26
Option 1 actually worked, I checked the opt folder and it already contains the lampp folder. Thanks again!

---

### Post by taurus on 2007-12-26
I thought you want to move the lampp directory in your $HOME/Desktop to /opt!  Then, why would you want to move the Desktop directory or root's?

What's the output of this command from a terminal again?

```
ls -la ~/Desktop/lampp
```

---

### Post by Dreamy1 on 2007-12-26
> **taurus said:**
> I thought you want to move the lampp directory in your $HOME/Desktop to /opt!  Then, why would you want to move the Desktop directory or root's?


I was going to move it from the document root to desktop and then finally find the opt folder but that was unneeded anyway so I edited my post, everything is working fine now. Except one problem I have which I have taken a screenshot here. 

[http://img264.imageshack.us/img264/7063/screenshotmozillafirefonr1.png](http://img264.imageshack.us/img264/7063/screenshotmozillafirefonr1.png)

> 
What's the output of this command from a terminal again?

```
ls -la ~/Desktop/lampp
```

Here's a screenshot

[http://img407.imageshack.us/img407/9376/screenshotstevenubuntuuoy2.png](http://img407.imageshack.us/img407/9376/screenshotstevenubuntuuoy2.png)

---

### Post by taurus on 2007-12-26
You need to look at /opt/lampp/htdocs/xampp/index.php because there is an error with line 2 in there.  I bet you don't have permissions to write to /opt/lampp?

```
cat /opt/lampp/htdocs/xampp/index.php
```


*NOTE:  Make sure it is the permissions or owner problem before you change them...

You can change the ownership of /opt/lampp from root to your login name, steven, if you wish.

```
sudo chown -R steven:steven /opt/lampp
ls -la /opt
```

---

### Post by Dreamy1 on 2007-12-26
I think its got to do with Permissions but I'm not to sure yet, I'll use a screenshot to make it simpler

[http://img182.imageshack.us/img182/8291/screenshotstevenubuntuuyi1.png](http://img182.imageshack.us/img182/8291/screenshotstevenubuntuuyi1.png)

I changed it to my login name and still nothing, are you sure I haven't missed anything yet?

---

### Post by taurus on 2007-12-26
It probably has something to do with permissions and ownership of that directory, /opt/lampp.  Where did you download it anyway?  Maybe it will tell you who should own that directory.

---

### Post by Dreamy1 on 2007-12-26
I downloaded it off the official website, which directed me to Sourceforge.

Interestingly I got the index to work by changing some permissions by right clicking properties -> permissions and setting a few options on the xampp folder, but when I proceed I am met with other errors, so I think I have to individually change the permissions of each file.

Update: Now I have other problems, which I really involve the software so I'll go pop over their forums for some advice on this issue. Though I'll come back here if I have something else regarding permissions. Thanks. :)

---

