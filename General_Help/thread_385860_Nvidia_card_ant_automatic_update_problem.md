---
title: "Nvidia card ant automatic update problem"
date: 2007-03-16
forum: General Help
---

### Post by abba567 on 2007-03-16
i run auto update and now after a reboot it has cause problems with my nvidia graphics card, it wont let me boot into the graphical interface how can i fix it?

---

### Post by gh0st on 2007-03-16
Was is it a kernel update by any chance? When the last kernel update was released I found it broke my video drivers. I use Nvidia as well. I had to reinstall the drivers.

I used a script called Envy and it fixed everything great. You can get it from this site: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

There should be a guide on how to run Envy there. You basically wget the envy deb file and then you can run it. If you need more step by step instructions just let me know and I'll post some.

Hope that helps :)

---

### Post by abba567 on 2007-03-16
Have looked at Envy but it appears to be a graphic interface and i cannt get that far all i can get is a text interface

---

### Post by abba567 on 2007-03-16
Have looked at Envy but it appears to be a graphic interface and i cannt get that far all i can get is a text interface

---

### Post by gh0st on 2007-03-16
It does have a graphical interface but it also has a text interface as well. In fact I've never used the graphical interface, it was only added recently. If you run Envy in the terminal or outside of the xserver it has a text based menu system.

I couldn't load the xserver either, I just logging in using the terminal prompt it gives you instead then ran envy to install the driver I needed and sort out my xorg.conf.

It does work, I know it does.

---

### Post by dannyboy79 on 2007-03-16
when you boot up, enter your username and password at the command line prompt. then do sudo nano /etc/X11/xorg.conf.
scroll down using the page down or down arrow, until you find "nvidia" for the device driver, change this to "vesa" or "nv". in nano, hit control x, it will ask if you want to save the file, click on y, then it'll ask if you want to save it to the origianl name, click on y again. now while in the terminal, type in 
sudo shutdown -r now
this should properly shutdown and  restart your machine. this should get you into a gui environment, then download envy and you should be set after you run it. if you get failure about it loading the nvidia module, make sure you have xorg-xserver-dev installed. good luck

---

### Post by gh0st on 2007-03-16
Log into the text interface that loads when xserver fails and try this:

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb

```

To download the Envy deb

```

sudo dpkg -i  envy_0.9.1-0ubuntu3_all.deb

```

To install it

```

envy

```

To run it and follow the menu. 

You can edit the xorg.conf yourself if you want, there's nothing wrong with doing that. I just found this way a lot quicker and easier. It's all personal preference though, whatever works for you.

Good luck :)

---

### Post by dannyboy79 on 2007-03-16
AMEN to that. I completely forgot about wget. I use it all the time when I am ssh'd into my box from work. how did you find out the url though? I have sometimes right-clicked on a file I wanted to download and selected save shortcut, then I go to my putty session and just paste it in with sudo wget obviously but then the download get's garbled for some reason and it's not a binary file anymore or something like that. it happened with a zip file that had dekstops pics in it. after I did the wget, it wouldn't be recognized as a zip but when I just downloaded it thru gui, it was fine? not sure what happened there but I guess my main question is, how to find out url's for wget. thanks

---

### Post by abba567 on 2007-03-16
Sorry Gh0st the first line of your code doesnt work any ideas?

---

### Post by dannyboy79 on 2007-03-16
well I just checked it for ya, it is

but first, do you have wget installed?

```
sudo aptitude install wget
```

and then, follow his instructions.

```
sudo wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
```

it appears as though his line

```
sudo dpkg -i envy_0.9.1-0ubuntu3_all.deb
```

may have had an extra space which may have prevented it from working. also, you need to make sure you run the above command from whatever folder this .deb was downloaded to, it should be your home directory, but if it's not, you can do

```
sudo find / -name envy_0.9.1-0ubuntu3_all.deb
```


to find it, once you find it, you just "cd" into that directory and run the dpkg command. that's it.

---

### Post by abba567 on 2007-03-16
sudo wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

This line still doesnt work it cant recognise envy_0.8.2-0ubuntu1_all.deb please help

---

### Post by dannyboy79 on 2007-03-16
you are just gonna have to get back to a gui so that you can make sure you have all the repo's enabled? follow this first:
[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

so you are going to have to do what I suggested earlier and manually update your /etc/X11/xorg.conf and change the "driver" from nvidia to vesa or nv. that should get you into the gui (it's actually called a window manager) for ubuntu.

I did notice that I was having you download an old version because I thought that's how you were suppose to do it for the text based install but I was wrong. I will however tell you that that is not why it's not working! I don;'t know why your command isn't working. the website is here  ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) once you get into the window manager. good luck

---

### Post by gh0st on 2007-03-16
> **abba567 said:**
> Sorry Gh0st the first line of your code doesnt work any ideas?

Sorry I was slow getting back to you, been offline a few hours. Did that work for you in the end?

In answer to DannyBoy79's earlier question I didn't use wget to find the URL I'm afraid I cheated a bit ;) . I used Firefox to find the url and write it down when I was locked out of xserver last time. It would be a lot easier if Envy was in the main repos and you could apt-get it instead, I don't think you can though. It would be cool to be able to find a url automatically with wget though you're right.

There may have been a stray space in my posted code somewhere so apologies for that. It works on my system though. I thought wget was installed as part of the normal Ubuntu install? Maybe I'm wrong, I use Edgy and I'm pretty sure it was installed with the main system.

Let me know if you are still having trouble with Envy and I'll see what I can do

EDIT: If you are still having trouble, can you give us any more information? What do you see on your screen? Is there a specific error message, that might help. The URL should definitely work.

---

