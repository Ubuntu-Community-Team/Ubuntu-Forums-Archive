---
title: "dual boot misbehavior Lenovo T450"
date: 2020-07-07
forum: General Help
---

### Post by pjnoxon2 on 2020-07-07
I have a Lenovo T450 with Windows 10 and I recently put Ubuntu Studio on there with a dual boot.

The first oddity is that when running Windows and I shut the lid (hibernate) and then later on open the lid it goes to Grub Boot menu. In the past with other laptops it was different, whichever OS was running would resume when I opened the lid. This would be just a minor annoyance, but there is something else.

I have Thunderbird on Windows. It has been running fine before I put the dual boot on here. I just use this to check all my e-mail accounts in the morning and use my other Windows 10 laptop to actually do correspondence later in the day. I always close Thunderbird before I hibernate (if it is not locked up, of course). Now when I run Thunderbird in Windows it will lock up the Lenovo sometimes. I tried uninstalling Thunderbird and reinstalled it, but it happened again today. At first the setting was to sleep when I shut the lid but I thought this might be wrong so I changed it to hibernate instead because that is what I always used before on other laptops that were dual boot. This didn't change the behavior of going to Grub, which is what I had hoped for. It still goes to Grub when I open the lid after booting up and running Windows and then going to hibernate by shutting the lid. It also didn't apparently fix the problem with Thunderbird. Thunderbird goes out to fetch new e-mail, looks like normal behavior with the mouse still movable, but it never returns control to Windows - and pressing Ctl-Alt-Del will not bring up the Task Manager.

Anyone else experience dual boot hibernate difficulty with Windows 10 and Ubuntu Studio on Lenovo T450?

---

### Post by pjnoxon2 on 2020-07-07
Maybe the problem is I don't wait long enough after I close T-bird and before I close the lid?

I mean as far as the locking-up, the going to Grub is the main focus here.

---

### Post by GhX6GZMB on 2020-07-07
First: Hibernate is not installed in Ubuntu, you'll need to set it up.
But do you really mean "hibernate"? This usually means pressing the power button when resuming (hibernate is suspend to disk and shut down).
Perhaps you mean "suspend", which is save to RAM and sleep, but stay under power?

---

### Post by pjnoxon2 on 2020-07-07
That's interesting to know, I'll have to look into this in Ubuntu. I know in Windows yes I mean hibernate as
I usually wake from hibernate at least once a day but not always so I don't want the Thinkpad to run the
battery all the way down. On my Asus if it was sleeping and the battery ran too low it would wake itself and
hibernate but I felt this was more risky than necessary. And then I had a laptop with a dead battery and no
one wants that. Right now I have Ubuntu Studio for software programming with an Arm toolchain, and I am
not working with that so I always shut down. When I get busy with that I would want to hibernate Ubuntu.

Right now I am curious about this going to Grub when coming out of hibernate in Windows, I don't remember
that on the Asus so I wondered about the Thinkpad. If no one has experience with it I guess I can always shut down.

---

