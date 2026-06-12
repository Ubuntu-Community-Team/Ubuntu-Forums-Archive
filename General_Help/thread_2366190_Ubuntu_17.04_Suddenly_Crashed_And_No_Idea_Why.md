---
title: "Ubuntu 17.04 Suddenly Crashed And No Idea Why"
date: 2017-07-14
forum: General Help
---

### Post by schuften on 2017-07-14
[TABLE]
[TR]
[TD="class: votecell"]         
   [/TD]
[TD="class: postcell"]        I've had 17.04 running for months just fine. It's "Always-On" 24/7.  It's set to automatically log on so there is never a log on screen  during boot up should I reboot. Yesterday it was running perfect. I went  to check the mail. When I returned, I was faced with the log in screen  and even that was frozen. I rebooted numerous times. Here's what I get.

  Black screen----maroon options screen----maroon blank screen----black screen----with message box. 

  
Error: (Click to dismiss. Also printed to stderr) File error: No such file or directory, gnome 

I click on the message box and it goes away. Then I am left with just a black screen.

  [B]
The last change I made in Ubuntu[/B]? With each new  upgrade (17.04) I lose my sound, pulseaudio problems. Eventually it  starts working if I just wait it out. A month ago I used Ubuntu Software  Center to remove pulseaudio. After several minor updates over the past  month and a reboot or two. I decided to use Ubuntu Software Center to  reinstall pulseaudio. I had yet to reboot after performing this single  task. It's been days since I made that install.

  
So anyways. I'm stuck flat footed not knowing where to go from here. 

     
[/TD]
[/TR]
[/TABLE]

---

### Post by Coto_Paxi on 2017-07-15
It looks like I have a very similar problem, although I am using ubuntu 14.10. 

I manage to log in, then PulseAudio (pavucontrol) opens up and displays: "Establishing connection to PulseAudio. Please wait........."

The absolutely ONLY program I manage to execute is the Opera web browser, and NOTHING ELSE.

From what I managed to read in other forums, the PulseAudio configuration files seem to be corrupted and they are slowing the whole system down violently. I my case I can't even open the terminal to type "sudo killall PulseAudio".

Am I posting in the right thread, or should I open a new thread?

Thanks for your help.

---

### Post by Coto_Paxi on 2017-07-15
shuften, can you reboot from an external operative system, for instance a USB stick?

If you can you could try to delete the PulseAudio configuration files.

Good luck!

---

### Post by jim_deadlock on 2017-07-16
It's no good trying to kill pulseaudio without disabling autospawn also:

~/.config/pulse/client.conf #or /etc/pulse/client.conf

autospawn=no

... then do

pulseaudio -k

... and it should then stay disabled.

---

