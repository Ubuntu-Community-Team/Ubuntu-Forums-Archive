---
title: "date and hwclock different"
date: 2007-04-28
forum: General Help
---

### Post by Xmister on 2007-04-28
I had a topic in feisty develop forum, but it's closed, so I open a new one.
My problem is that the clock seeks a lot.
I think the kernel count the seconds wrong, because my date and hwclock output different after a while.
I tried to set the system to use UTC, but didn't helped.
Some output in typing order:
```
$ uptime
 17:22:42 up  4:04,  1 user,  load average: 3.13, 2.53, 2.54

```
```
$ date
2007. ápr. 28., szombat, 17.22.53 UTC

```
```
$ hwclock
2007. ápr. 28., szombat, 17.21.44 UTC  -0.371474 másodperc

```

---

### Post by Xmister on 2007-04-28
Now I have edited the sudoers to run hwclock --hctosys command without password prompt, and I set cron to run this command in every minutes, and it doing it, but when it's changing back the clock with a second(that's the different in every minutes). All programs pause for a second.
I think it would better to make the kernel to count the seconds well, or at least set cron to run the command in every 5 seconds, I think in 5 seconds there isn't too many differences so it might not cause a pause.

---

### Post by Xmister on 2007-04-29
Any ideas? Now the difference is a hour(A had to stop the cron, because that way every multimedia thing was unenjoyable)

---

### Post by Xmister on 2007-05-03
Nobody? Just me that unlucky? I can't belive this! No suggestion, no idea. I was left alone :(

---

### Post by Xmister on 2007-05-13
In windows there is no problem with it, so I think it is not too hard to get it normally work.

---

### Post by persoontje on 2007-05-13
You could try to sync your clock with a timeserver, but that doesn't really solve your problem, but you would get the correct time I think.

---

### Post by code3x on 2007-05-13
I've got the exact same problem. I was about to post a new thread but just found this one:

I recently completely re-formatted and installed feisty (I was previously on edgy) and now the clock runs slower than it should, probably by around half a second or so. If I start the timer on my watch at the same time as my computer clock rolls over to the next minute, by the time my watch reaches one minute the computer clock is already 20 seconds behind.

After seeing this thread I also compared date and hwclock with the same results as Xmister. 

Does anyone have any ideas on how to fix this properly?

---

### Post by Xmister on 2007-05-13
I have a half-solution, well it's not really a solution, but the end of it the same.
1.Go to a console and type sudo gedit /etc/sudoers and write tihs line to the end of it:
> yourusername ALL = (ALL) NOPASSWD: /sbin/hwclock
replace yourusername with your username.
Log out, and log in again
2.make a time.sh file in your home directory with this content:
> #!/bin/sh
while (true) do
sudo hwclock --hctosys
sleep 0.1
done

make it executable: chmod +x ~/time.sh
3. You should do the following procedure after every boot:
Then press Ctr+F1 to get a console, login and type ~/time.sh
After that press Ctrl+F7 to get back to X.

This will synchronize the unix clock with the hwclock in every 0.1 second

---

### Post by Xmister on 2007-05-22
Now I'm from live cd, and here everything is OK. The clock is ticking in rigth speed.
So I guess there is a software problem with my installation, but I don't know what can speed up the clock

---

### Post by Xmister on 2007-05-25
I made some backup and repartitioned all of my winchesters(I like starting from clean) and put on a XP(Just for games) and an Ubuntu of course.
I checked the clock and it was still going faster then it should, but not that faster as on my old system.
I remembered I tried to disable acpi on my previous system and it was made the clock slower on it, but my machine frost after a little time, so I turned it off, but now without acpi the clock goes as fast as it should, and my system is going without any problem(moreover without it I have suspend and some progs working better than with it).
So now it's working well.
For those who want to disable acpi:
> gksudo gedit /boot/grub/menu.lst
At the end of the file you should see something like this:
> title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a2dccf5b-b9db-4b9c-b8cf-e7429a2dac9f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
In it you should change 
> kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a2dccf5b-b9db-4b9c-b8cf-e7429a2dac9f ro quiet
with
> kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a2dccf5b-b9db-4b9c-b8cf-e7429a2dac9f ro quiet acpi=off
And reboot. That's it.

---

### Post by dodgePT on 2007-05-25
I noticed that problem this morning, the only diference was that mine was 10 minutes early, not late...

---

