---
title: "Boot takes 10 minutes, without activity"
date: 2008-05-16
forum: General Help
---

### Post by boterbram on 2008-05-16
Hi

I just did a fresh install of xubuntu 8.04 (twice, same problem) and I have got a problem. After the grub menu I get the black screen with "Starting up..." in the upper-left corner, and that's it for exactly 10 minutes (I timed it). After 10 minutes the system boots as normal. Now I figure some program is waiting 10 minutes because of the exact timing and no sounds/lights flickering from my computer. What can it be or where do I start?

gr Bram

---

### Post by imbjr on 2008-05-16
Try the recovery mode boot operation from the GRUB menu. You should then see what your machine is doing and where it stalls.

---

### Post by boterbram on 2008-05-16
Allright, did the recovery mode startup, but I again didn't get any output other than "Starting up ..." and then the 10 minutes of nothing and then the starting of all kinds of processes (normal startup I guess), what now?

I didn't have this problem with the live cd by the way

---

### Post by boterbram on 2008-05-16
I allready tried adding different bootoptions like nosplash, noapic and all_generic_ide (I needed this in 7.10), but all without succes, the problem seems to be before the splash screen has to come up, but I don't know what happens before that. Does anybody know if Grub produces the "Starting up ..." text or is that xubuntu already? Or any other ideas?

---

### Post by erginemr on 2008-05-16
I wish I has an answer, but here are two links with the same problem:
[https://answers.launchpad.net/ubuntu/+question/23973](https://answers.launchpad.net/ubuntu/+question/23973)
[http://ubuntuforums.org/showthread.php?t=528741](http://ubuntuforums.org/showthread.php?t=528741)

None of them packs any solution, but both point to some hard drive (SATA/IDE) config problem...:confused:

---

### Post by boterbram on 2008-05-16
> **erginemr said:**
> I wish I has an answer, but here are two links with the same problem:
[https://answers.launchpad.net/ubuntu/+question/23973](https://answers.launchpad.net/ubuntu/+question/23973)
[http://ubuntuforums.org/showthread.php?t=528741](http://ubuntuforums.org/showthread.php?t=528741)

None of them packs any solution, but both point to some hard drive (SATA/IDE) config problem...:confused:

Thanks for the reply, although the first one is not the same problem, because this person is talking about waiting 3 hours, while my waittime is strictly 10 minutes, after which xubuntu works normally. I will try rootnoverify as suggested in the second thread though, whish me luck;)

---

### Post by boterbram on 2008-05-16
No luck with rootnoverify:(

---

### Post by housam on 2008-05-16
Try the solution in this [[COLOR="Red"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580903")

---

### Post by boterbram on 2008-05-19
> **housam said:**
> Try the solution in this [[COLOR="Red"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580903")


Yes, I tried deleting the splash and quiet stuff, not working, any other ideas?

---

### Post by boterbram on 2008-05-19
Bootchart output, might it be helpful:

[[IMG]http://www3.picturepush.com/photo/a/697851/220/697851.png[/IMG]](http://www.picturepush.com/public/697851)
[http://www3.picturepush.com/photo/a/697851/img/697851.png](http://www3.picturepush.com/photo/a/697851/img/697851.png)

---

### Post by imbjr on 2008-05-19
> **boterbram said:**
> Allright, did the recovery mode startup, but I again didn't get any output other than "Starting up ..." and then the 10 minutes of nothing and then the starting of all kinds of processes (normal startup I guess), what now?

I didn't have this problem with the live cd by the way

Durn. So the problem appears to be occurring during initramfs if I understand my linux boot sequence correctly. Unfortunately, I'd just be stabbing in the dark if I attempted to help now.

---

### Post by boterbram on 2008-05-20
"Het initramfs bevat om deze redenen kopieën van relevante configuratie-files, zoals udev en modprobe config. Met update-initramfs -u maak je een nieuwe initramfs met de huidige configuratie."
Oh wait, that is in Dutch (it is from [http://gathering.tweakers.net/forum/list_messages/1257355/last](http://gathering.tweakers.net/forum/list_messages/1257355/last))

It says you can make a new initramfs by typing update-initramfs -u, could this be of any help you think?

---

### Post by imbjr on 2008-05-20
> **boterbram said:**
> "Het initramfs bevat om deze redenen kopieën van relevante configuratie-files, zoals udev en modprobe config. Met update-initramfs -u maak je een nieuwe initramfs met de huidige configuratie."
Oh wait, that is in Dutch (it is from [http://gathering.tweakers.net/forum/list_messages/1257355/last](http://gathering.tweakers.net/forum/list_messages/1257355/last))

It says you can make a new initramfs by typing update-initramfs -u, could this be of any help you think?

Try reading the translated version, if your Dutch is is about as good as mine i.e. nil-nu-mouth:

[http://translate.google.co.uk/translate?u=http%3A%2F%2Fgathering.tweakers.net%2Fforum%2Flist_messages%2F1257355%2Flast&sl=nl&tl=en&hl=en&ie=UTF-8](http://translate.google.co.uk/translate?u=http%3A%2F%2Fgathering.tweakers.net%2Fforum%2Flist_messages%2F1257355%2Flast&sl=nl&tl=en&hl=en&ie=UTF-8)

---

### Post by latna on 2008-05-20
This is just a shot in the dark, and I don't know much about your setup, but you don't have any other solution yet.

I once had a problem booting when I built a new system. It would take about 10 minutes to boot as you say. I traced the problem to a misconfigured jumper on my hard drive. I set the jumper to master when I should have set it to single. It took a long time to boot because it was looking for the slave device but there was none there.

Worth a shot i guess.

---

### Post by HermanAB on 2008-05-20
Bad network configuration?  Try unplugging the network cable, so that the network startup will fail more quickly.

---

### Post by boterbram on 2008-05-25
> **HermanAB said:**
> Bad network configuration?  Try unplugging the network cable, so that the network startup will fail more quickly.


I tried this, but no luck, exactly the same issue

---

### Post by boterbram on 2008-05-25
> **latna said:**
> This is just a shot in the dark, and I don't know much about your setup, but you don't have any other solution yet.

I once had a problem booting when I built a new system. It would take about 10 minutes to boot as you say. I traced the problem to a misconfigured jumper on my hard drive. I set the jumper to master when I should have set it to single. It took a long time to boot because it was looking for the slave device but there was none there.

Worth a shot i guess.

Sounds promising, ill try it when I've got some more time, it could well be this is the problem, because I put the harddisks in myself and I was not sure where to put the jumper on one of them. The only thing is that I never seemed to have any problems with this, only untill i installed xubuntu 8.04 instead of 7.10/openSuse/puppylinux/whatever i tried, any ideas on why that is so?

---

### Post by boterbram on 2008-05-25
> **imbjr said:**
> Try reading the translated version, if your Dutch is is about as good as mine i.e. nil-nu-mouth:

[http://translate.google.co.uk/translate?u=http%3A%2F%2Fgathering.tweakers.net%2Fforum%2Flist_messages%2F1257355%2Flast&sl=nl&tl=en&hl=en&ie=UTF-8](http://translate.google.co.uk/translate?u=http%3A%2F%2Fgathering.tweakers.net%2Fforum%2Flist_messages%2F1257355%2Flast&sl=nl&tl=en&hl=en&ie=UTF-8)

I prefer the dutch version, the "english" translation is really difficult to understand:P but what it basically says you can make a new initramfs, but it seems to be something not to mess up and because I haven't got any experience with this i was wondering if it would be smart to try and rebuild the initramfs?

---

