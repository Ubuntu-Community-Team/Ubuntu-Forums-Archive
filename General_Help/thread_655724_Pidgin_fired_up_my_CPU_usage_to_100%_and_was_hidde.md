---
title: "Pidgin fired up my CPU usage to 100% and was hidden. Any ideas?"
date: 2008-01-01
forum: General Help
---

### Post by jesushero on 2008-01-01
I was running Pidgin and firefox together. When I quit firefox the computer was running very slow. I brought up the system monitor which showed the CPU usage to be at a constant 100% on CPU2 and about 10% on CPU1. The 512mb of RAM are almost constantly used at 40% anyway, so it looked normal. My swap partition is 20GB large (what a waste of space).

I quit pidgin which was still responding, slow as the rest of the system but definitely not frozen. The CPU was still at 100% and no process appeared to be using it in the System Monitor. I brought up the terminal and used top. It revealed a process called pidgin using 100% of the CPU. This process was not visible in System Monitor. I killed it with -9 and it worked immediately bringing my system back to normal. Why was it hidden in the first place? And why was it still running (at 100% cpu cost) while the pidgin gui had successfully disappeared?

Of course after a few minutes X crashed as usual so I had to log on again. (any ideas about this would also be appreciated).

While we're at it, any ideas on how to mount a CD/DVD disc overriding the permissions of the files written in it?? I want to be able to access everything on CD/DVD's.

Thanks in advance.

---

### Post by empthollow on 2008-01-01
that's weird, have you tried running pidgin since then? does it seem to be a recurring problem or more of a fluke.  also, you mentioned that X crashes alot. Is there a problem with the X installation?

---

### Post by jesushero on 2008-01-01
Thanks for replying. I've been running pidgin a lot and usually it runs fine. It sometimes crashes, but nothing like that. This was a one-off thing, but I was a bit worried by the CPU usage. Pidgin is not what I would consider a heavy program! When Cinelerra renders videos, CPU usage is at 95-96%. I've NEVER before seen my CPU usage rise to 100%.

X tends to crash every now and then, I am not sure why. I had posted another thread about it but nobody had any ideas. I have not tampered with X at all, it was what came with the Ubuntu studio installation. I am not very familliar with how X works. I've been to the wiki page but did not find anything helpful there. I have installed all updates up to now, not sure if any of those was X related but this problem has always been since I installed Gutsy. Do you think I could benefit from installing a different version of X??

Firefox tends to crash most of all, it is extremely unstable and there's no log entries about that. X-related log entries mention a problem with Keyring manager, although I have never used that. I used to experience total freezes but one of the updates stopped those. I think it had to do with several library updates. Now total freezes are very random and only happen about once a week, usually relating to heavy video use. My nvidia geforce graphics card seems to be overheating after extended heavy graphics use (except if it is normal for it to be too hot to touch).

To get the picture, total freezes once a week, x crashes once every 2 days and firefox crashes 10 times a day...

One user mentioned powernowd but I the boot log entries say it is not being used because my processor does not support it.

Any ideas would be greatly appreciated, I am relatively new to linux (especially the graphic interfaces)...

---

### Post by empthollow on 2008-01-01
i expierence total freezes on occasion always relating to heavy usage.  it doesn't happen to me often.  x for me does not crash very often otherwise. i don't think a different version of X would make a difference and i'm not sure there is on in the repos - if not it's probably more trouble than it's worth-. i would try a reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```
there may be a setting out of wack.  also what video drivers are you using?

i can't think of anyting that would cause pidgin to take that much cpu except for some sort of glitch.  If it was hidden maybe the windows was closed and it didn't know how to shut down that time or something.  If it works fine since i would probably just chauk it up to a random glitch.

oh, can you give me a link to your post about X

---

### Post by Speckay on 2008-01-14
For the pidgin error, my laptop ends up having a similar pidgin problem, but it hogs 100% of the CPU all the time, regardless of what I'm doing with it. If I look in the processes tab under System Monitor, it says pidgin is "sleeping", even if it's open and in use, and takes whatever is remaining from the CPU. It will stay like this until I quit pidgin, then everything returns to normal right away.

Can anyone help? I'm kind of a noob with Linux. :)

---

