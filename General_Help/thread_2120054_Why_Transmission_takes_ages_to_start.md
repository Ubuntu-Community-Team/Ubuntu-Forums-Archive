---
title: "Why Transmission takes ages to start?"
date: 2013-02-25
forum: General Help
---

### Post by uzumakifahim on 2013-02-25
Normally, I use Qbittorrent, but recently I have downloaded Transmission to use as my default torrent client, as it is lightweight than Qbittorrent.

Now, after installing Transmission I am facing a weird problem. It's taking so much time (5-7 minutes) to start the application. It's working good enough, but problem with the starting.

Please suggest me, how can I get rid of this issue. Thanks to all.

---

### Post by carl4926 on 2013-02-25
It should take just a few seconds to start.

Try launching it from the terminal: transmission
See if there is any feedback

Are you using KDE? Seeing that you mentioned QT

---

### Post by lisati on 2013-02-25
Do you have some torrents that you have already downloaded that transmission might be checking?

---

### Post by uzumakifahim on 2013-02-25
Thank to all for trying to help me.

@carl4926, I don't know how to run an application from terminal. Could you please tell me what is the exact command to launch transmission from terminal?

@lisati, there is no torrents to check for tranmission. It's taking ages to start from the very first time after installation.

---

### Post by mikewhatever on 2013-02-25
> **uzumakifahim said:**
> Normally, I use Qbittorrent, but recently I have downloaded Transmission to use as my default torrent client, as it is lightweight than Qbittorrent.

Now, after installing Transmission I am facing a weird problem. It's taking so much time (5-7 minutes) to start the application. It's working good enough, but problem with the starting.


Downloaded Transmission from where? Your profile says Ubuntu 12.04, so Transmission should have been pre-installed. Can you fill us in on that.

---

### Post by carl4926 on 2013-02-25
As others said
Transmission is already installed

To start it as I suggested.
Open a terminal and type in:

transmission

Hit enter

---

### Post by uzumakifahim on 2013-02-26
Actually, I use Qbittorrent as my default bit torrent client. That's why after installing Ubuntu 12.04, I've removed Transmission and install Qbittorrent from Ubuntu Software Center. At that time I've used Transmission for few days. Then it worked fine. 

Now I'm interested to use Transmission as my default bit torrent client, but this time I'm facing this problem.

I'm using Ubuntu 12.04 with Unity desktop.

@carl4926, this is the output when I tried to open Transmission from terminal

```
fahim@fahim-Desktop:~$ transmission
transmission: command not found
fahim@fahim-Desktop:~$ 

```

---

### Post by carl4926 on 2013-02-26
sorry it's

```
transmission-gtk
```

---

### Post by carl4926 on 2013-02-26
> **carl4926 said:**
> sorry it's

```
transmission-gtk
```

And you should have installed

transmission-common
transmission-gtk

---

### Post by uzumakifahim on 2013-02-26
@carl4926, Thanks for the correction. Here is the output.

```
fahim@fahim-Desktop:~$ transmission-gtk
connect: Connection timed out
connect: Connection timed out
connect: Connection timed out

```

Every line appears about 50 seconds interval and after the third line Transmission actually starts.

---

### Post by uzumakifahim on 2013-03-05
My problem have been solved. After giving the previous command on terminal and after rebooting my PC, my problem has been solved magically. So, I'm marking this post as solved.

If there is anyone, who can say the reason of how this solution works, you are very welcome to post.

Thanks to all.

---

### Post by Phalkon on 2013-06-19
I have never unistalled the transmission. It worked just fine, but then somehow I had the same issue with 5min starting. I ran the command "transmission-gtk" and now its fine (it took a little longer to close it, but its not that insanly long as the starting was).
When I ran the command (transmission-gtk) it started instantly without any output in terminal.
Its really mysterious. Thanks for help anyway. :)

---

