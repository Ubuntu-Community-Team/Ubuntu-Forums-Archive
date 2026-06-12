---
title: "Help? 14.04 freezes/unfreezes every 5 secs after snapd install"
date: 2021-05-15
forum: General Help
---

### Post by clevertomato on 2021-05-15
I have a Dell notebook PC that has run Ubuntu 14.04 64-bit desktop fine for years. I haven't upgraded because there's been no need. I depend on this for many of life's important and daily demands.

I recently decided to try Bitwarden password manager. I found information that stated it was installable on 14.04 via snap if snapd was first installed.

At a CLI I executed:

sudo aptitude install snapd

After that completed, I executed:

sudo snap install bitwarden

I rebooted, then tried to run bitwarden. It failed to start, giving a screen full of errors. This is when I noticed the PC freezing up every 5 seconds for 5 seconds at a time (then unfreezing, then repeating). I wanted to get out of this mess fast, so I executed:

sudo snap remove bitwarden

And then

sudo aptitude remove snapd

Then I rebooted, but the repetitive freezing up won't go away. It's not just the input of the keyboard or mouse, either. When I ssh into the PC from another device, activity freezes the same way... Frozen for 5 seconds, unfrozen for 5 seconds.

I realize this is an older version of Ubuntu and maybe nobody will be interested in this odd problem, but if anyone has any helpful suggestions of how I may undo this dysfunction that was triggered by installing snap (presumably), I would be very grateful.

--S

---

### Post by GhX6GZMB on 2021-05-15
Talk about shooting yourself in the foot.

Personlly I hate snaps and the first thing I do is to remove snapd.

But installing it on that old a version is... well, risky.

---

### Post by Tadaen_Sylvermane on 2021-05-15
You need to run supported software for any real help here. 14.04 went EOL 2 years ago. That was when you "needed" to upgrade.

---

### Post by HermanAB on 2021-05-15
Well, you are running Linux.  There is no need to wonder what is going on.  You don't have to stumble around in the dark in a coal mine.  You can see every process and exactly how much memory/CPU cycles it consumes.  You can then kill any running process and see what happens after you killed it.

Run 'top' and kill any suspect process with 'kill -9 PID'.  After a while you will kill something important and will have to reboot - don't worry about it.  Eventually you will find the problem process and then you can look for a permanent solution.

---

