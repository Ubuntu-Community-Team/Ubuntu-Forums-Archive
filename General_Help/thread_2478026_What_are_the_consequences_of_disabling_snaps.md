---
title: "What are the consequences of disabling snaps?"
date: 2022-08-14
forum: General Help
---

### Post by supersaiyan880 on 2022-08-14
Hi! :D

I'm planning on doing a fresh installation of Ubuntu 20.04.4 and I have a question.

(I haven't decided on the flavour yet but I think it doesn't matter for this question (please tell me if it does))

I'm thinking of disabling snaps after the fresh install using this commands:

```
sudo systemctl stop snapd.service
sudo systemctl mask snapd.service

```

(followed by a restart)

and enabling them again if I need them or if I need to install any snaps with this commands:

```
sudo systemctl unmask snapd.service
sudo systemctl start snapd.service

```

(followed by a restart)

I took the commands from here [https://askubuntu.com/a/1269770](https://askubuntu.com/a/1269770)

I think I've read I won't be able to run the default installation of Firefox and that's OK.

I'm also planning on installing other stuff I will use like Android Studio or VSCode using .deb or flatpak, avoiding snaps.

But, is there any other consequences I should be aware of before disabling snaps on Ubuntu?

Thanks in advance!

---

### Post by Tadaen_Sylvermane on 2022-08-14
You will just run into walls that may be hard to get past. I think much of the vanilla Ubuntu DE is snap based already. You can probably work around some of it with a different DE or something. Ubuntu is heading toward snaps in general it seems so you may be better off going to a different distro altogether. Debian is a good choice I made that jump, albeit not because of snaps.

---

### Post by guiverc on 2022-08-14
I've QA-tested a number of ways of disabling snaps, and responded here & there, and did not encounter any problems, at least in the short term.

I can't recall any issues back in 20.04 (*focal*), and wouldn't want to comment there as it's been so long since I really used it.  Sure I'm aiming to find time to do a 20.04.5 QA-test install later today, but that's still not really using & especially living with it.

A recent answer I gave can be found here (Lubuntu 22.04 LTS & avoiding snaps), where 

[https://discourse.lubuntu.me/t/avoiding-snaps-in-lubuntu-22-04/3506](https://discourse.lubuntu.me/t/avoiding-snaps-in-lubuntu-22-04/3506), which links to other prior posts including on removing the `firefox` snap & replacing it with the *deb* package version which is why I did a reasonable amount of testing.  I experienced no issues myself, but you'll note I mention the potential of '*laying a minefield*' for yourself, that may create issues in the future.

How much of a minefield will depend on what release, and what *flavor* you're talking about. I'd expect fewer issues with *focal* (20.04) than *jammy* (22.04), but again the *flavor* does matter, as well as packages you'll install on your box.

To me, none of the *minefield* would be a real concern, except primarily, that I risk getting some error in the future that just *bewilders* me, as you cannot expect the error message to explicitly state the reason is because you disabled *snap**d*. Sure once you realize the cause, you can re-enable *snapd* and the error that you were *fighting* will be gone, but how much time was lost/wasted until you thought of the *snapd* connection....  If you're capable of remembering, seeing the connections pretty quickly; the *hurdle* of course will be a lot less, ie. if you think of various Ubuntu tools, are you aware of what the *requirements* and assumptions are  (my usual example is [ubuntu-release-upgrade]("https://launchpad.net/ubuntu/+source/ubuntu-release-upgrader")r though as it's a tool we rarely use, having problems only when it comes time to *bump* release to something newer isn't exactly a huge burden.. esp. if you document what you did well).

Also please don't forget *flavors* only come with 3 years of support; thus 20.04 reaches EOL for *flavors* in 2023-April.  Five years applies to packages from 'main' and not really 'universe' (community sourced including all *flavors*). Sure if you're offline, this won't matter, just consider it if security matters to you.

Myself, I've made some boxes *snap free* and had no issues (*which includes a focal box that was snap free for I forget how long, but well over a year*), but ended up returning to using *snap packages* as in some circumstances they just make sense, and save me time.  I'm also a Debian user, and my  Debian *bookworm* desktop has *snapd* on it too, as do some other Debian boxes (*bullseye* etc). 

Yes I do consider *flavor *matters rather significantly, as some rely on *snap* packages for their tools, welcome, software stores etc, so you'll need to replace the *flavor* tools with other packages if you remove/disable *snapd*.  You can just look at the *manifests* for a *flavor* ISO to see how much they rely on *snap* packages, even if not an absolute guide, it'll give a pretty good & quick *glimpse*.

The programs, and what you'll use the box for also matter. 

The consequences are easily managed though... you just cannot forget you've disabled *snapd* when you want to use some of the Ubuntu tools, or if you forget, recall the weird error you're getting maybe the consequence of your *snapd* decision, and will disappear the moment you re-enable *snapd *functions, which to me is a easily managed thing.

My 2c.

(*flavors:  I can think of two where the effect is extremely minimal/none, and one at least where its rather significant; and that's just the flavors I'm somewhat aware of...*)

---

### Post by VMC on 2022-08-15
I didn't use the "masking" that you showed, but purged snapd. I will never use snaps. I use the firefox-*.tar.bz2 that doesn't use snaps, found here:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

---

### Post by HermanAB on 2022-08-15
If you don’t like Ubuntu, use another distro that better suits your needs.  There are so many, one of them should fit.

---

### Post by The Cog on 2022-08-15
I used **[FONT=Courier New]sudo apt purge snapd[/FONT]** when I was using Xubuntu 20.04 and had very few issues. I just had to install firefox/chromium from other sources. 

However, with Ubuntu and its variants increasing their use of snaps, I tried Mint which has good reviews and promises not to use snaps. I was pleasantly surprised, and settled there. If you are really against snaps, then finding another distro is probably the best path. If you can live with snaps, then Ubuntu and its variants are still pretty good.

---

### Post by ajgreeny on 2022-08-15
I've been using Xubuntu for many years now and for the last two LTS versions I have done what VMC does.

No snaps for me on my admittedly fairly old machines with spinning HDDs meaning snaps are too slow to open.
I have had no problems or difficulties at all so far; as for the future, who knows?

---

### Post by yaminb on 2022-08-15
As others have said, if you want to disable snaps, why not use a different distribution. This is especially true since you are doing a fresh install.
Will you experience problems? I haven't heard of any, but if more things become snaps, then I could see it causing issues.

That said, you can certainly minimize your use of SNAPs. I basically let Ubuntu do whatever it needs to as far as the default use of SNAPs. 
I choose a minimal Ubuntu install, but that has nothing to do with SNAPs. I just prefer doing it that way
I don't like to break from the 'default' part of the distro.

I generally choose flatpaks for any applications I add myself.

---

### Post by SeijiSensei on 2022-08-15
I, too, have removed snapd from (Kubuntu) systems with no obvious consequences. I rely on official PPAs like those at Mozilla for applications like Firefox and Thunderbird, or compile from source in extremis.

---

### Post by supersaiyan880 on 2022-08-15
> [COLOR=#000000]Also please don't forget [/COLOR][I]flavors only come with 3 years of support; thus 20.04 reaches EOL for [I]flavors in 2023-April. Five years applies to packages from 'main' and not really 'universe' (community sourced including all [I]flavors). Sure if you're offline, this won't matter, just consider it if security matters to you.
[/I][/I][/I]

I didn't know the flavors had less support time. Thank you guiverc, that will help me decide, and also thanks for the detailed answer.

---

### Post by supersaiyan880 on 2022-08-15
> **yaminb said:**
> As others have said, if you want to disable snaps, why not use a different distribution. This is especially true since you are doing a fresh install.
Will you experience problems? I haven't heard of any, but if more things become snaps, then I could see it causing issues.

That said, you can certainly minimize your use of SNAPs. I basically let Ubuntu do whatever it needs to as far as the default use of SNAPs. 
I choose a minimal Ubuntu install, but that has nothing to do with SNAPs. I just prefer doing it that way
I don't like to break from the 'default' part of the distro.

I generally choose flatpaks for any applications I add myself.

Thank you.

Maybe this is what I'm going to do.

I'm also thinking about setting every new network connection as 'metered' to avoid automatic updates, which is the specific reason I want to avoid snaps. This is what I do with my Windows installation.

---

