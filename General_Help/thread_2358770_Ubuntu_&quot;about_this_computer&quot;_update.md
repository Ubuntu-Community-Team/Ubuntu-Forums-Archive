---
title: "Ubuntu &quot;about this computer&quot; update"
date: 2017-04-17
forum: General Help
---

### Post by Karolina.K on 2017-04-17
Hello

My dell xps 9360 came with ubuntu 16.04 and I have now updated to
17.04 but the about this computer still shows the 16.04, with the dell logo and such, 

How do I change this to say 17.04?

Thanks
/karolina

---

### Post by Bucky Ball on 2017-04-17
Open a terminal and post the output of 

```
lsb_release -a
```

That will confirm you have successfully upgraded. How did you upgrade it? A clean install of 17.04? Guess so as 16.04 LTS doesn't directly upgrade to 17.04 as far as I know, unless you upgrade to 16.10> 17.04. Please confirm.

---

### Post by Karolina.K on 2017-04-17
it shows 17.04 on other places just the about this computer that shows 16.04,  yes i updated from 16.10 to 17.04

---

### Post by vasa1 on 2017-04-17
> **Karolina.K said:**
> ... the about this computer still shows the 16.04, with the dell logo and such, 
...
More details of what you mean by "and such" and a screenshot even from a cell phone may help!

---

### Post by Karolina.K on 2017-04-19
OKay here is what it shows, but system is 17.04, [http://imgur.com/a/7zNmf](http://imgur.com/a/7zNmf)

---

### Post by Bucky Ball on 2017-04-19
... and you still haven't posted the output of this.

```
lsb_release -a
```

---

### Post by howefield on 2017-04-19
I think the System Settings overview pulls the image from /usr/share/unity-control-center/ui/UbuntuLogo.png, Your posted image looks like a "Dell'ified" adaptation of the usual .png image.

What's the output of

```
apt-cache policy unity-control-center
```

I think the installed version should be 15.04.0+17.04.20170402.6-0ubuntu1

---

### Post by vasa1 on 2017-04-19
> **Karolina.K said:**
> OKay here is what it shows, but system is 17.04, [http://imgur.com/a/7zNmf](http://imgur.com/a/7zNmf)
If you don't mind, please use the forum attachment facility for images. It's the paperclip icon above the posting area. Here's a look at imgur's connections (trackers, ads, etc) :)

---

### Post by Karolina.K on 2017-04-19
First command shows this:

```
karolina@karolina-XPS-13-9360:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty
karolina@karolina-XPS-13-9360:~$ 
```

Second shows this: 

```
karolina@karolina-XPS-13-9360:~$ apt-cache policy unity-control-center
unity-control-center:
  Installed: 15.04.0+17.04.20170402.6-0ubuntu1
  Candidate: 15.04.0+17.04.20170402.6-0ubuntu1
  Version table:
 *** 15.04.0+17.04.20170402.6-0ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
        100 /var/lib/dpkg/status
```

I can't seem to find /share/ folder in /usr/

---

### Post by howefield on 2017-04-19
Thanks for the output.. you can search for the file with

```
dpkg -S /usr/share/unity-control-center/ui/UbuntuLogo.png
```

which should output.. 
 
```
unity-control-center: /usr/share/unity-control-center/ui/UbuntuLogo.png
```

basically telling you which package the file is installed from.

Or open the image with 

```
eog /usr/share/unity-control-center/ui/UbuntuLogo.png
```

You have a few choices, firstly to live with it as it is purely cosmetic, secondly to replace the image file or thirdly to purge and replace the unity-control-center package.

Try opening the file with eog first to double check that is what the problem is and then we can sort out the best way to correct it if that is what you want to do.

---

### Post by Karolina.K on 2017-04-19
How do i replace the image?, I was thinking to fix it and then update it

Nevermind, found it and updated it with Gimp so now everything looks fine :) thanks for the help

---

### Post by howefield on 2017-04-19
> **Karolina.K said:**
> How do i replace the image?, I was thinking to fix it and then update it

Well, I know you said you had upgraded to 17.04 and that would be presumably recently but I'd do it the other way round, update to see if that fixed it and if not, then replace the image.

```
sudo apt update
```
```
sudo apt dist-upgrade
```

just to double check that you are absolutely up to date.

If still an issue, you could download the 17.04 package, extract the .png and copy over. Did you manage to open the current file with eog as above?

To download the package to your ~/Downloads folder..
```
wget http://se.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_15.04.0+17.04.20170402.6-0ubuntu1_amd64.deb -P ~/Downloads
```

Then right click the downloaded .deb package and select open with Archive Manager, double left click on the data.tar.xz file and navigate through to ./usr/share/unity-control-center/ui/UbuntuLogo.png and then highlight and extract that single file your folder of choice, probably ~/Downloads is as easy as any.

Make a copy the original file with..

```
sudo mv /usr/share/unity-control-center/ui/UbuntuLogo.png ~/Pictures
```

in case you need to put it back and finish by copying the new file with..

```
sudo mv ~/Downloads/UbuntuLogo.png /usr/share/unity-control-center/ui/
```

Apologies, that looks more difficult/complex than it actually is, for ease I've attached the .png file to this post.

---

### Post by howefield on 2017-04-19
> **Karolina.K said:**
> Nevermind, found it and updated it with Gimp so now everything looks fine :) thanks for the help

Ah, missed your edit having had the thread and my unfinished reply open in another tab.

Cool, I didn't consider that "fourth" option but glad you got it and thanks for marking the thread as solved. :)

---

### Post by Karolina.K on 2017-04-19
no problem :)

---

