---
title: "Can't install teamviewer 7"
date: 2013-05-07
forum: General Help
---

### Post by mahmoud moosa on 2013-05-07
Hello everybody,

I am using Ubuntu 64-bit, when i tried to install temviewer 7 it showing me error in the attached screenshot.

any idea please ?

Thank you for any help.

Mahmoud[ATTACH=CONFIG]242309[/ATTACH]

---

### Post by mahmoud moosa on 2013-05-08
Hello everybody,

When i used bash to download it, i've got this output.
Please take a look.

[ATTACH=CONFIG]242317[/ATTACH]

I've tried manay solutions from previous posts, but doesn't work with me.

Thank you.

---

### Post by slickymaster on 2013-05-08
Are you trying to install a 32bit copy into a 64bit machine?

Download the [correct .deb]("http://download.teamviewer.com/download/teamviewer_linux_x64.deb") and try to install it with:
```
sudo dpkg -i teamviewer_linux_x64.deb
```

---

### Post by mahmoud moosa on 2013-05-08
Hello and welcome,

No, i want to download 64-bit version.
I will give it a try and will let you know.

Thank you for your help.

---

### Post by mahmoud moosa on 2013-05-08
> **slickymaster said:**
> Are you trying to install a 32bit copy into a 64bit machine?

Download the [correct .deb]("http://download.teamviewer.com/download/teamviewer_linux_x64.deb") and try to install it with:
```
sudo dpkg -i teamviewer_linux_x64.deb
```

Hello and welcome, 

No, i want to download 64-bit version.
I took your advise, and i got the error attached in the screen shot.

What wrong is going on ? any idea ? 

Thank you for your help.

[ATTACH=CONFIG]242341[/ATTACH]

---

### Post by slickymaster on 2013-05-09
> **mahmoud moosa said:**
> Hello and welcome, 

No, i want to download 64-bit version.
I took your advise, and i got the error attached in the screen shot.

What wrong is going on ? any idea ? 

Thank you for your help.

[ATTACH=CONFIG]242341[/ATTACH]

What's wrong is the fact that your sudo command is incorrect, you wrote _sudo dpkg -i teamviewer_linux_64.deb._ but you are missing the character 'x' before 64.deb. See my previous post and what notice the difference.

It's preferable that you copy/past the right command from here to your terminal window:
```
sudo dpkg -i teamviewer_linux_x64.deb
```

---

### Post by mahmoud moosa on 2013-05-09
> **slickymaster said:**
> What's wrong is the fact that your sudo command is incorrect, you wrote _sudo dpkg -i teamviewer_linux_64.deb._ but you are missing the character 'x' before 64.deb. See my previous post and what notice the difference.

It's preferable that you copy/past the right command from here to your terminal window:
```
sudo dpkg -i teamviewer_linux_x64.deb
```


Hello my friend,

you are correct, i took copy from your command and paste it in bash but still the same error.

[ATTACH=CONFIG]242372[/ATTACH]

Thank you for your help.

---

### Post by slickymaster on 2013-05-09
From the image you attached, I see you are running the _sudo dpkg -i teamviewer_linux_x64.deb_ command in your home folder. Is it the downloaded teamviewer_linux_x64.deb there? You have to run the command in the folder where the package is.

If you have downloaded it to the **~/Downloads** folder then before running the command you have to cd into that folder.
```
cd ~/Dowloads
sudo dpkg -i teamviewer_linux_x64.deb
```

---

### Post by The Spectre on 2013-05-09
Why are you trying to install an old version of TeamViewer?

TeamViewer 8 has been available for quite a while now...
[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

It may be easier to just download the DEB File and install it...
[http://download.teamviewer.com/download/teamviewer_linux_x64.deb](http://download.teamviewer.com/download/teamviewer_linux_x64.deb)

---

### Post by mahmoud moosa on 2013-05-09
> **The Spectre said:**
> Why are you trying to install an old version of TeamViewer?

TeamViewer 8 has been available for quite a while now...
[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

It may be easier to just download the DEB File and install it...
[http://download.teamviewer.com/download/teamviewer_linux_x64.deb](http://download.teamviewer.com/download/teamviewer_linux_x64.deb)

Hello my friend,

Your opinion is nice, but a friend of mine using version 7 that's why both we should have the same.

Thank you for your help.

---

### Post by mahmoud moosa on 2013-05-09
Hello everybody,

Partially, solved with shown command:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

Until here the main problem is solvd but why when i want to install it showing me error again ?

Please have a look


[ATTACH=CONFIG]242387[/ATTACH][ATTACH=CONFIG]242388[/ATTACH][ATTACH=CONFIG]242389[/ATTACH]

---

### Post by The Spectre on 2013-05-09
> **mahmoud moosa said:**
> Hello my friend,

Your opinion is nice, but a friend of mine using version 7 that's why both we should have the same.

Thank you for your help.
Version 8 can connect to Version 7 but not the other way around.

So depending on which way the connection needs to be made one of you can have Version 8.


Here is the link to Version 7...

[http://download.teamviewer.com/download/version_7x/teamviewer_linux_x64.deb](http://download.teamviewer.com/download/version_7x/teamviewer_linux_x64.deb)

---

### Post by slickymaster on 2013-05-10
> **mahmoud moosa said:**
> Hello everybody,

Partially, solved with shown command:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

Until here the main problem is solvd but why when i want to install it showing me error again ?

Please have a look


[ATTACH=CONFIG]242387[/ATTACH][ATTACH=CONFIG]242388[/ATTACH][ATTACH=CONFIG]242389[/ATTACH]

Regarding your first screenshot, did you proceed as I explained in my post #8?

---

### Post by mahmoud moosa on 2013-05-10
> **slickymaster said:**
> Regarding your first screenshot, did you proceed as I explained in my post #8?

Hello my friend,

Even tried from Download folder and still the same error showing.


[ATTACH=CONFIG]242418[/ATTACH]

Thank you.

---

### Post by slickymaster on 2013-05-10
The problem is simple. As you previously installed teamviewer7:i386, which is the 32 bit version, and haven't uninstalled it, and now you are trying to install teamviewer_linux_x64.deb, which is the 64 bit version, your system is complaining about that.
So first you have to remove the 32 bit version:
```
sudo apt-get purge teamviewer7

```

Afterwards proceed with the install of the correct package as I post previously.

---

### Post by mahmoud moosa on 2013-05-12
> **slickymaster said:**
> The problem is simple. As you previously installed teamviewer7:i386, which is the 32 bit version, and haven't uninstalled it, and now you are trying to install teamviewer_linux_x64.deb, which is the 64 bit version, your system is complaining about that.
So first you have to remove the 32 bit version:
```
sudo apt-get purge teamviewer7

```

Afterwards proceed with the install of the correct package as I post previously.

Worked perfect. the problem basically from begining when i installed Ubuntu, it wasn't connected to the internet that's why there were missing many many OS packages and libraries.

What i did is, clean install as well as followed the good man  **[COLOR=#006400]slickymaster[/COLOR]** advise. :)

Thank you and for all other members replies.

Greatful.

Mahmoud

---

