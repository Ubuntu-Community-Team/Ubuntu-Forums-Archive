---
title: "“Segmentation fault (core dumped)” when i try to execute an executable Ubuntu 14.04"
date: 2014-06-21
forum: General Help
---

### Post by user16 on 2014-06-21
I downloaded from [http://www.bio-tracking.org/category/software](http://www.bio-tracking.org/category/software) the Ubuntu executables (application/x-executable)  that i wanted but when i try to execute them in terminal the message "Segmentation fault (core dumped)" appears.
Their site mentions that they are designed for Ubuntu 12.04 so i tried executing them on Ubuntu 12.04 in VirtualBox and they worked.
Does anyone have any idea what might be the difference in these OS that can't let them be executed in 14.04 ?
Maybe it's because i am a new Ubuntu user but it seems normal to me that executables that run in an older version should be able to run in later versions too.

---

### Post by dragonfly41 on 2014-06-21
I get these segmentation errors when debugging Python code ..

follow the tip here .. to get more information on the source of the error.

[https://bugs.launchpad.net/bzr-gtk/+bug/923824](https://bugs.launchpad.net/bzr-gtk/+bug/923824)

hack .. usr/share/pyshared/gobject/constants.py .. to temporarily bypass the segmentation error report.

You will need to restore this constants.py to default for other Python apps to work.

From your target website ...

> This open-source project makes use of the [OpenCV]("http://www.bio-tracking.org/category/software/opencv.org"), [PointCloud Library]("http://pointclouds.org/"), and [QT]("http://qt.nokia.com/products/") libraries.

you may need to install Qt library from Ubuntu Software Centre.

---

### Post by user16 on 2014-06-21
Yeah, but the main thing is that it runs perfect in Ubuntu 12.04 without the need to install any of these or even debugg. So i am guessing there is a dependency issue(?) which i have to override somehow. I am new to Ubuntu so i don't know how to bypass the error like you said.

Thanks for the response.

---

### Post by dragonfly41 on 2014-06-21
From the link I posted .. follow this workflow ..

Open the terminal .. (Ctrl+Alt+T) ..

Copy and paste this command ..

**[COLOR=#0000ff]sudo gedit /usr/lib/python2.7/dist-packages/gobject/constants.py[/COLOR]**

Insert your login password at sudo prompt ..

After a few seconds Gedit will launch showing contents of constants.py

After the line .. **[COLOR=#0000ff]import gobject._gobject[/COLOR]**

insert this syntax .. 

**[COLOR=#0000ff]raise ImportError('no static please')[/COLOR]**

Save the edited file.

When you now run your app you will now see in terminal the full backtrace which should point you to the source of the segmentation error.

After testing your app to see the backtrace
you may need to restore this file to its default by reopening in Gedit
and commenting out the line.

**[COLOR=#0000ff]# raise ImportError('no static please')[/COLOR]**

I've created a bash script which allows me to quickly set/reset this 
raise ImportError() during testing python code.

---

### Post by user16 on 2014-06-21
I did exactly what you said but it still shows the message "Segmentation fault core dumped" on terminal. So, i cannot see the backtrace.
Thanks a lot for your step by step response.
I think it might have something to do with the FFmpeg which is missing from Ubuntu 14.04 but that's just a guess.

---

### Post by user16 on 2014-06-22
Does anyone know how to backtrace that and see what the bug is so that i can fix it?
Or if someone can help me compile it from source (which i doubt i could accomplish).

---

### Post by dragonfly41 on 2014-06-22
Are you the author of this post .. ?

[https://groups.google.com/a/bio-tracking.org/forum/?fromgroups#!topic/discuss/y3e0jH0oC2Y](https://groups.google.com/a/bio-tracking.org/forum/?fromgroups#!topic/discuss/y3e0jH0oC2Y)

Clarify .. are you trying to install on 32 bit or 64 bit Ubuntu 14.04?

[COLOR=maroon][Later edit ..]

You wrote > so i tried executing them on Ubuntu 12.04 in VirtualBox and they worked.


so you* could *install VirtualBox on Ubuntu 14.04 and install Ubuntu 12.04 image as VM.
Then install on your VM in Ubuntu 14.04.[/COLOR]

...

Also .. have you read this ...

[https://github.com/biotracking/biotrack/wiki](https://github.com/biotracking/biotrack/wiki)

> Currently we support **Ubuntu 12.04** environments.


and here ...

> Setup

This guide assumes that you are starting with a fresh install of **Ubuntu 12.04**. 

No mention of **Ubuntu 14.04**.

---

### Post by user16 on 2014-06-22
Yes, i am the author of the mentioned post.
I assume an Ubuntu 14.04 64bit OS and i tried executing the software on Ubuntu 12.04 32bit in VirtualBox. 
Yes, the software was never updated from when it was released for 12.04 so i am guessing there is a compatibility issue with ubuntu 14.04.

The thing is the software is really slow in virtualbox and not practical since i cannot transfer files with my main OS and the guest OS.

I thought the solution might be easy that's why i made that post but i guess it's more complicated.

---

### Post by dragonfly41 on 2014-06-22
Short of taking the step of migrating the app from Ubuntu 12.04 to 14.04, if the app is important you could dualboot Ubuntu 12.04 and Ubuntu 14.04 on different partitions.  Or have Ubuntu 12.04 on an external drive or USB. Unetbootin would help with this.

Avoiding VirtualBox.

And you could use a shared folder between Ubuntu 12.04 and Ubuntu 14.04. Or use Spideroak.com to share.

---

### Post by dragonfly41 on 2014-06-23
Final thought ...

It may be that just installing 32 bit library in your Ubuntu 14.04 (64 bits) might cure your problem.

I only use Ubuntu 12.04 (32 bits) so I can't test the biotracking software.

But read here ...

[https://stackoverflow.com/questions/23182765/how-to-install-ia32-libs-in-ubuntu-14-04-lts](https://stackoverflow.com/questions/23182765/how-to-install-ia32-libs-in-ubuntu-14-04-lts)

---

### Post by user16 on 2014-06-23
Thank you for your time.

I tried your last suggestion. I installed the 32bits libraries but still the same issue. I will probably dual-boot Ubuntu 12.04 and 14.04.

---

### Post by user16 on 2014-06-23
Thank you for your time.

I tried you last suggestion. I installed the 32bits libraries but still the segmentation fault appears. 

Maybe it has something to do with the FFmpeg which is missing from Ubuntu 14.04.

I will dual boot Ubuntu 12.04 and 14.04 as a solution i guess.

---

### Post by dragonfly41 on 2014-06-23
If you just google "ubuntu 14.04 FFmpeg" you'll find a few tutorials on installing.

---

### Post by user16 on 2014-06-23
Yeah, tried that too following one of the tutorials, but nothing. Still the segmentation fault.

---

### Post by mc4man on 2014-06-23
Likely nothing to do with ffmpeg, ect. as the app provides all it's own libs inc. those from ffmpeg
More likely a glibc error, nothing you're going to do about that & the project is at best dormant.
(so 12.04 or not at all.

---

### Post by dragonfly41 on 2014-06-24
> The thing is the software is really slow in virtualbox and not practical since i cannot transfer files with my main OS and the guest OS.

If you still want to try running your biotracking app on Ubuntu 12.04 (32 bit ?) as guest OS on VirtualBox within Ubuntu 14.04 (64 bit ?) host OS you might benefit from some tweaking in VirtualBox ..

[http://askubuntu.com/questions/207813/why-does-a-ubuntu-guest-in-virtualbox-run-very-very-slowly](http://askubuntu.com/questions/207813/why-does-a-ubuntu-guest-in-virtualbox-run-very-very-slowly)

Consider how much memory you are applying. How much RAM do you have?

Use System Monitor in both Ubuntu 14.04 (host) and Ubuntu 12.04 (guest) to inspect RAM usage when running VM.



[p.s.]

And you might try installing Spideroak.com on both host and guest OS (VM) to share files between guest and host.

---

### Post by nadine3 on 2014-06-26
I have the same problem with NS2 
[h=2]segmentation fault (core dumped)[/h]

---

