---
title: "Teamviewer 13 will not load gui in 18.04"
date: 2018-08-17
forum: General Help
---

### Post by Robbyx on 2018-08-17
I had the same problem with 16.04 so today I upgraded to 18.04. When run from the command line this in what I see. Do you know how to get the teamviewer gui to work? I have tried restarting the daemon but to no effect. 

> ~$ teamviewer

Init...
CheckCPU: SSE2 support: yes
Checking setup...
Launching TeamViewer ...
Launching TeamViewer GUI ..

---

### Post by RichardLinx on 2018-08-18
How did you go about installing it? I just downloaded the .deb and it's running fine: [https://imgur.com/a/akRKjwe](https://imgur.com/a/akRKjwe)

After installing and running it for the first time I was prompted with a license agreement, and then able to run the program. Were you prompted with the license agreement the first time? Have you tried installing/running both the 64 and 32 Bit versions?

---

### Post by cmcanulty on 2018-08-18
won't work for me either. I try install with gdebi and as soon as I click in install gdebi crashes

---

### Post by #&amp;thj^% on 2018-08-18
Open up terminal and enter:

```
sudo apt install gdebi-core
```

Download latest TeamViewer package
we will use wget to download the latest TeamViewer package:

```
wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
```

Install TeamViewer

```
sudo gdebi teamviewer_amd64.deb
```

Answer y when prompted.
Also you will see errors if you are using Wayland.  Might be better to disable wayland.
```
sudoedit /etc/gdm3/custom.conf
```
And change the line:

```
#WaylandEnable=false
```

TO:
```

WaylandEnable=false
```

---

### Post by cmcanulty on 2018-08-18
thanks it is working now

---

### Post by Robbyx on 2018-08-19
I have made the changes and for me it is still not working. The gui does not fully load.

This is what also happens when I try the command line:

>  
robins@robins-desktop:~$ teamviewer

Init...
CheckCPU: SSE2 support: yes
Checking setup...
Launching TeamViewer ...
Launching TeamViewer GUI ...



I am wondering if I should remove every aspect of Teamviewer and start again. How do I find all the parts to delete?

---

### Post by #&amp;thj^% on 2018-08-19
> **Robbyx said:**
> 
I am wondering if I should remove every aspect of Teamviewer and start again. How do I find all the parts to delete?

That's worth a shot.
```
cd /
rm -rf /home/*/.local/share/teamviewer* /home/*/.config/teamviewer /opt/teamviewer
cd ~
wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
sudo gdebi teamviewer_amd64.deb
```
Are you running on Wayland?

---

### Post by Robbyx on 2018-08-19
The idea of stripping out teamviewer and reinstalling has not made any difference.

I am running gnome xorg.

---

### Post by Robbyx on 2018-08-19
I tried running TV through the command line non installation option:

robins@robins-desktop:~/teamviewer$ ./teamviewer

Init...
CheckCPU: SSE2 support: yes
Checking setup...
Launching TeamViewer ...
Starting network process (no daemon)
Network process already started (or error)
Launching TeamViewer GUI ...

That didn't work as well.

---

### Post by Robbyx on 2018-08-21
Bump

---

