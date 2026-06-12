---
title: "I've managed to lock up the terminal"
date: 2021-06-12
forum: General Help
---

### Post by JohnnyC44 on 2021-06-12
My terminal is being held by an apt-get command and is doing nothing. All I was doing was installing the restricted extras on my new system. I'm using 20.04.3. How do I kill the process? BTW I am just getting back into Ubuntu after years and years. Consider me a newbie again.

---

### Post by &amp;KyT$0P# on 2021-06-12
Probably not a good idea to kill it.

If you have gnome-system-monitor installed you should be able to use that to at least see the process: select "All Processes" (and check "Show Dependencies" so you can see what is running this [FONT=Courier New]apt-get[/FONT]).

Do you have [FONT=Courier New]unattended-upgrades[/FONT] installed?

---

### Post by JohnnyC44 on 2021-06-12
unattended-upgrades is not installed.

---

### Post by &amp;KyT$0P# on 2021-06-12
So what does System Monitor show as the parent process for this rogue [FONT=Courier New]apt-get[/FONT] ?

Does the rogue [FONT=Courier New]apt-get[/FONT] have any child processes?

---

### Post by JohnnyC44 on 2021-06-12
I have no clue which of the hundred processes the system monitor is showing me is the culprit. I was downloading and installing the Ubuntu extras when the process was interrupted. Here is another screenshot showing the point of the apt-get lock. If I remeember correctly, these are the MS fonts. Sorry, think of me as a newbie.

---

### Post by Impavidus on 2021-06-13
If apt-get is installing Microsoft fonts and appears to be doing nothing, it's probably displaying a license agreement and waiting for you to accept it. It's a classic text based menu. You can interact with it using the keyboard. Try the arrow keys or tab to select a button, hit enter to push it.

If you already killed the apt-get process (by closing the terminal, or by rebooting), the lock may be dangling. In that case it should be safe to manually remove it. Then installation of the package must be completed with```
sudo apt install -f
```

---

### Post by JohnnyC44 on 2021-06-13
And to manually remove it?

---

### Post by HermanAB on 2021-06-14
Open another terminal, find the name of the beast and hang it up:
$ top
# sudo kill -SIGHUP PID

It doesn’t matter if you kill the ‘wrong’ thing.  You can always reboot.

---

### Post by ajgreeny on 2021-06-14
If the Microsoft font package is the one causing this problem you may find it easier to use synaptic package manager to install them as it does provide a GUI for agreeing to the license.

A reboot before doing this should ensure that you can continue with this process if you can't continue with it  straight away.

---

### Post by JohnnyC44 on 2021-06-14
Thank you, everyone. I have the terminal back and synaptic made installing the MS fonts a breeze, so it looks as if I'm good to go. I appreciate all the help -- and trust me, I need all the help I can get here.

---

