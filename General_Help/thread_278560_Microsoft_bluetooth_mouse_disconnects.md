---
title: "Microsoft bluetooth mouse disconnects"
date: 2006-10-16
forum: General Help
---

### Post by Clark Nova on 2006-10-16
I have a Microsoft bluetooth mouse which is working almost perfectly. The only problem that I have with it is that it goes into hibernation every so often to preserve battery life and then I have to reconnect to it with:

sudo hidd --search

Is there a way that I can make it connect on startup and stay connected? Perhaps it's just not possible though, does anybody have any ideas?

Thanks :)

---

### Post by Clark Nova on 2006-10-16
Is there anybody else that has found a way to fix this?](*,)

---

### Post by nrgtek on 2006-10-22
I get the same problem on my Suse 10.1 desktop. I also can't use the side buttons or wheel button. Can you paste me what your xorg.conf looks like for your Ubuntu desktop so I can compare the 2?

---

### Post by zerohalo on 2006-10-27
I experience the same problem, running Dapper with a Logitech V270 bluetooth mouse. After a few minutes of inactivity (not sure how many exactly), it goes off.

I have to "reset" the mouse, and then run:

$ sudo hidd --connect <address>

it's unfortunate that I can't connect without sudo as it requires me to type my password just to reconnect the mouse.

Any solutions?

---

### Post by linedpaper on 2006-11-22
i have the same problem.  anyone come up with a solution yet?

---

### Post by novaraz on 2007-01-02
My Microsoft BT mouse is the same.  I made a little script to reconnect, but this is rather annoying.  The same mouse stays connected in FC6, even after system restarts.

Is there a timeout variable or something somewhere??

---

### Post by linedpaper on 2007-01-03
mine no longer disconnects, sadly i have no idea what i did to get it to work.  i remember reinstalling all bluetooth modules as well as editing some text file.  i found the answer somewhere in these forums, but can't remember where.

---

### Post by zerohalo on 2007-01-11
Edit /etc/default/bluetooth and change HIDD_OPTIONS line to the following:

HIDD_OPTIONS="-i --connect <addr> --server"

where <addr> is the bluetooth mac address of the mouse.

---

### Post by BatteryKing on 2007-01-14
I think I figured out what exactly is going on with bluetooth mice under 6.10.  I examined the /etc/init.d/bluetooth file and noticed some configuration options where done directly in that file.  These configuration options seemed to be overriding the ones in /etc/default/bluetooth.  Once I changed the options in /etc/init.d/bluetooth (hidd_enable=1 and optionally HIDD_OPTIONS="-i --connect <addr> --server" [where <addr> is the MAC address of the bluetooth mouse]) my mouse started working just as good as it did in 6.06, which is quite well.

---

