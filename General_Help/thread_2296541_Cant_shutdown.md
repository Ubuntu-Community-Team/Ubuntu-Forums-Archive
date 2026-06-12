---
title: "Cant shutdown"
date: 2015-09-26
forum: General Help
---

### Post by tirafesi on 2015-09-26
Hello all!

I installed ubuntu today, but i cant shutdown my computer. The only way i can do it is by pressing the power button.

Now, i've already spent 3 hours trying to fix this thing, so please don't tell me to do what the other 999 posts i read say.

what i've tried:
sudo shutdown
sudo shutdown -h 0
sudo gedit /etc/default/grub and edit that line that says quiet splash. i've left it blank, i've added acpi and apm, i've added reboot=bios

The last log i get is:
[COLOR=#141823][FONT=helvetica]"reboot: Power down"
[/FONT][/COLOR]
So, can anyone please let me know how to fix this?

---

### Post by SuperFreak on 2015-09-26
Try ```
shutdown -h now
```

---

### Post by QDR06VV9 on 2015-09-26
Lets start with getting some needed information so we can help you.
Please install inxi.
```
sudo apt-get indstall inxi
```
then post back the results of in the terminal
```
inxi -Fxz
```
Regards

---

### Post by tirafesi on 2015-09-26
"sudo shutdown -h now" doesnt work

here are the results from inxi:
[http://i.imgur.com/0txgQPu.png](http://i.imgur.com/0txgQPu.png)

Also, i already had this problem BEFORE installing ubuntu. When i booted ubuntu from a flash drive wihtout installing it, i got this same problem

What should i do?

---

### Post by tirafesi on 2015-09-26
Well, turns out "sudo shutdown -h now" does work! :D
Thank you!

Do i need to write it everytime i wanna shutdown my pc now? Is there a way i can just shutdown as usual wihtout needing to write it on the terminal?

---

### Post by SuperFreak on 2015-09-26
Not an ideal solution but you can open terminal screen and use keyboard arrow key to find the command without having to type it out.
Best to find the root of problem. Check this [THREAD]("http://ubuntuforums.org/showthread.php?t=2217602") post #4

---

### Post by tirafesi on 2015-09-26
Didnt work. 
(i had to write update-grub instead of grub-update, not sure thats relevant)

What now? :/

---

### Post by tirafesi on 2015-09-26
Nvm, i didnt read the whole post... It worked like that guy said. But it means i still need to press the power button to completly shut it down...
Isnt there a way to just normally shutdown the computer? :/

---

### Post by SuperFreak on 2015-09-26
Sorry I couldn't be of more help, it may be a bug with 14.04 and your particular PC

---

### Post by tirafesi on 2015-09-26
Well, found another problem...
Seems like if i use the solution in that post, my wi-fi doesnt connect...

Guess i'll stick to the "sudo shutdown -h now"...

Thanks for the help :)

---

### Post by desukane on 2015-10-09
Here's a new or different logic... How do I remove, un-install, the guest session, makes me a bit paranoid. 14.04 worked brilliantly and simply for a long time. I re-installed because, I didn't and don't like what I'm seeing, weird things were and are occurring. It seems to be the only way I can shut down the new install is to play a game. I'd like to know why? I've found that if you  log out of guest and then shut down, 14.04 is normal. It seems to me to fix the problem is to remove the guest. How? and why is this occurring? It appears that the guest is more powerful than the administrator. There is a way to remove the guest, I just don't remember. Help...

---

### Post by desukane on 2015-10-09
Single click was a problem, too. The simplest trick was to move the page to the upper left corner. It took hours to figure this out. 14.04 has most everything you need. One just has to wade through the gibberish. Your or my forgetting can be a problem. Just a simple explanation can save folks a bunch of problems. It's always, what is.

---

