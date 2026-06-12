---
title: "Could not connect to ubuntu archive and fails to add even ppas"
date: 2012-12-01
forum: General Help
---

### Post by uzumakifahim on 2012-12-01
I'm using Ubuntu 12.04, suddenly Ubuntu update manager stopped updating.

At first I thought that, it's a problem with my Internet connection, but I was wrong, because downloading, browsing everything is perfect.

Then I've tried with ```
sudo rm -vf /var/lib/part/lists/partial/*
``` to remove my previous lists and update with a new one. Unfortunately, no luck with this, same problem continuing.

Moreover, recently I've tried to add Cinnamon PPA, but it failed to connect with the key server.

Then I've pinged to archive.ubuntu.com, that's perfectly OK.

I don't know what's the problem. Please help anyone. 

Thanks in advance.

---

### Post by ibjsb4 on 2012-12-02
What happens if you do a:

sudo apt-get update

---

### Post by uzumakifahim on 2012-12-02
Thanks for your reply. When I've tried with ```
sudo apt-get update
``` it take too much time to connect with the server. Most of list update is unsuccessful and finally it shows that some index file is missing and that's why the update is unsuccessful.

---

### Post by ibjsb4 on 2012-12-02
> **uzumakifahim said:**
> Thanks for your reply. When I've tried with ```
sudo apt-get update
``` it take too much time to connect with the server. Most of list update is unsuccessful and finally it shows that some index file is missing and that's why the update is unsuccessful.

I cannot tell what the problem is without seeing the output of the update command.  Please post the output in code tags.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=code+tags&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=code+tags&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by 2F4U on 2012-12-02
Can you try to select a different mirror in software sources? Your current mirror may be out of sync.

---

### Post by uzumakifahim on 2012-12-03
Thanks all of you for your help. Great news is that from today morning my problem has been solved automatically and my Ubuntu is on fire again. I'm marking this thread as solved.:)

---

