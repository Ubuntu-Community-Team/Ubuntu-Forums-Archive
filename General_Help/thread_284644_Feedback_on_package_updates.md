---
title: "Feedback on package updates"
date: 2006-10-25
forum: General Help
---

### Post by beerfan on 2006-10-25
My single biggest frustration with Ubuntu is the frozenness of package versions. The versions of software that are packaged when the distribution is released is the only version you can get from the official repositories and newer, less buggy versions of software is often not available in .deb package format.

I've already heard most of the responses you're going to repeat.

[LIST=1][*]"Testing and packaging all the applications in a repository is a big, complicated job and the manpower does not exist to continue this effort after a version has shipped." If this is true then it sounds like an indication that the distribution is being mismanaged. If the OS restricts what software I can install because the distributor lacks the resources to test and package it for me then something needs to be removed from the loop. Perhaps testing could be removed. Perhaps restructuring or switching the package manager would solve this. I read that the SMART package management system divides packages effectively separating the core packages that could destabilize the system if change from the end user applications which have little effect on the system when they experience a problem. I don't claim to know the solution though.

[*]"If you want to upgrade an application, just download the tarball and compile it." For the average user (i.e., someone who hasn't spent the last 4 years developing python applications) this is a very hit and miss prospect. More often than not the dependencies snowball all out of proportion, and that's when you can figure out what the dependencies are and which packages you need to install to get them. If I had the patience and experience to install from source I suppose I'd be a Gentoo user instead of an Ubuntu user.

[*]"Bleeding edge software is risky and freezing application versions ensures stability." While I appreciate that there is some truth to this statement I suspect that the risk is merely a symptom of a problem described above and upgrading certain classes of applications is not, itself, a risky action. Furthermore, what you might label bleeding edge is often incorrect (many application upgrades are not alpha or beta quality but are ignored anyway) and in fact is either behind or barely keeping pace with the functionality available on alternative operating systems. The only thing that is ensured by freezing versions of end user applications is that the installation will stagnate.
[/LIST]

I encounter very frustrating bugs in many applications (multimedia, wireless networking, etc.) and the worst part is that when I report the bug I am told, or discover, that the bug was fixed 3 versions ago and I should simply upgrade. "Well, I would love to but...I run Ubuntu and I would have to upgrade my entire OS to install the latest version of your program."

Overall, I am a happy Ubuntu user and I wouldn't be giving feedback if I didn't want it to succeed but there are times when the frustration level rises too high to ignore. I appreciate that distributing open source software is a complex task and the aptitude system does an admirable job of handling it but I believe there is plenty of room for improvement. I hope that some of you will reconsider how improvements can be introduced.

---

### Post by meng on 2006-10-25
I think it's great that you've posted on this topic, and presented some excellent arguments. My immediate responses, for what they're worth (i.e., not much) are:
1) I agree very much with "your" point #3. I'd add that software which depends on other programs can be very sensitive to version changes (as I discovered previously with DVDStyler, I had to *downgrade* my mjpegtools in order for DVDStyler to work.
2) Certain compromises have to be made for a Linux which is "for the masses". I'm not saying the current situation is perfect, far from it, but I doubt that the extreme bleeding-edge scenario would be more suitable for most users.
3) On the subject of "most users", when it comes to added functionality of newer versions of programs, I doubt that most users miss much by having an older version. Hardware compatibility may be the exception though, we could sure use broader compatibility.
4) There's always Debian etch or if you're truly adventurous, sid. (Sure, you could take that to mean, "If you don't like it, take your bat and ball and go home," but that's not what I intended!)
Like you, I often lament the delay in upgrading to new software versions. But I either live with what I'm given or else go and upgrade the damn thing manually.

---

### Post by beerfan on 2006-10-26
If it wasn't clear from my original post, I am certainly not against upgrading things myself. In fact, I wish I had the capability to upgrade more things. For example, Network Manager on my laptop is barely tolerable (using wpa2 and an Atheros card) taking nearly a minute to connect to the AP and failing to reconnect if the signal is lost and after much time researching the problem and solution, and a failed attempt at upgrading the madwifi-ng driver, I had to give up and live with the current situation. Granted, drivers and networking isn't exactly edge software with no impact on the system (I could give other examples as well) but my point is to ask if most people simply live with their frustrating problems until the next release of the distribution?

I also wonder why some seemingly "core" packages (apache, ssh, openssl, gtk, qt, etc.) are updated (via update manager) but edge software, which should have far less impact on the system if a problem occurs, is never updated. I imagine it boils down to priority but it runs counter to the argument that allowing upgrades introduces risk.

I started using Dapper Drake a bit before it was released and I found it stable enough to make me consider upgrading to Edgy early as well. However, how do you know when it's too early to upgrade and when it's stable enough to commit a computer and installation time to? It took me quite a while to get all the software I need working (heck, I'm still in the process) and at this point I'm not exactly enthusiastic about the idea of a reinstall or upgrade.

---

