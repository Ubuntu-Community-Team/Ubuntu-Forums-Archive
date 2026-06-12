---
title: "Eventual upgrade from one LTS version to another"
date: 2007-01-03
forum: General Help
---

### Post by OrangeCrate on 2007-01-03
I've been reading with interest about the challenges some are experiencing with an upgrade from Dapper to Edgy. Out of curiosity, if a person decides to stay with an LTS version, how will he update to the next LTS version?

Will he have to upgrade through all of the individual versions in between, or would you expect that there will be a process to upgrade direct to the new LTS version from the old one?

For now, I'm quite pleased with the stability of Dapper, and am generally not attacted to new bells and whistles, if my current version works.

---

### Post by AlanRogers on 2007-01-03
Good question, watching this thread with interest!

---

### Post by OrangeCrate on 2007-01-03
Bump.

---

### Post by taurus on 2007-01-03
I am totally guessed on this but I don't suppose the next TLS would be out until the current one, Dapper, is expired, three years from when Dapper was released!  Therefore, it will be a while before you would see another LTS version!

---

### Post by Engnome on 2007-01-03
Well so far it has been recommended to update your dist +1 and then +1 again. But you can always try and replace all "dapper" with "whatever the next LTS will be called" and then dist-upgrade.

But TBH I have no idea, isn't the dapper the first LTS? Then it probably hasn't been decided yet how to upgrade.

---

### Post by OrangeCrate on 2007-01-03
Taurus,

Thanks for your response. Yes, I know that the next LTS version won't come out until after 6.06 expires. Though I thought my question was pretty straight forward, please allow me to reask the question in a different way...

Will there be a mechanism to upgrade directly to the next LTS version from this one when it's available, without having to use any of the versions that are released in between?

If the upgrades to newer versions are as buggy as this one from Dapper to Edgy appears to be, I'm not sure I want to upgrade to anything that comes out until the new LTS version. (See my original post in this thread for other info.)

Someone around there has had to think about this, so a comment from staff would be appreciated.

---

### Post by bodhi.zazen on 2007-01-03
> **OrangeCrate said:**
> Taurus,

Thanks for your response. Yes, I know that the next LTS version won't come out until after 6.06 expires. Though I thought my question was pretty straight forward, please allow me to reask the question in a different way...

Will there be a mechanism to upgrade directly to the next LTS version from this one when it's available, without having to use any of the versions that are released in between?

If the upgrades to newer versions are as buggy as this one from Dapper to Edgy appears to be, I'm not sure I want to upgrade to anything that comes out until the new LTS version. (See my original post in this thread for other info.)

Someone around there has had to think about this, so a comment from staff would be appreciated.

I cant help but ask WHY ?

If you want to stay with stable, LTS no problem.

When the next version is available, back up your data, do a fresh install, restore your data.

Problem solved.

That clearly is the cleanest solution. Why would you want to hassle with all those updates in between ?

---

### Post by OrangeCrate on 2007-01-03
> **bodhi.zazen said:**
> When the next version is available, back up your data, do a fresh install, restore your data.

That's what I thought I would do, but if what you say is true, why is anyone bothering to upgrade from Dapper to Edgy then?

Why not do as you've suggested right from the git-go, and save the hassle of the upgrade process? 

Anyway, I think that's the answer I was looking for. Thanks.

---

### Post by femto on 2007-01-03
Sorry to butt in but does anyone know why my upgrade has ground to a halt?

I have attached a partial screenshot to show you where I've got to.

All the files downloaded and then it appears to have simply...stopped. :-(

Is there something I've done wrong?

Thanks.

---

### Post by bodhi.zazen on 2007-01-03
Be patient !

How long have you waited ?

---

### Post by femto on 2007-01-03
Well, I clicked the "Upgrade" button in the Update Manager at about 6pm and it is now 11:20pm.... :-k

---

### Post by koenn on 2007-01-03
> If you want to stay with stable, LTS no problem.
When the next version is available, back up your data, do a fresh install, restore your data.
Problem solved.

It's not necessarily that simple, and the original question was a good one. 
Say you're working in an IT department somewhere, maintaining 250 ... 1000 ... ??? .... desktops. Obviously, you stick with an LTS version, because yoy want a stable environment. 
Say all these desktops a bit more than just the default LiveCD install : you've added applications, tweaked gnome a bit, modified network config to suit your needs, modified some config files here and there to fix or optimize something, and so on. 

Eventually, you'll want to upgrade to the next LTS release.
In such a case, a clean install and start from scratch may be not your first choice. 

I know the next LTS release is still 2.5 years from now, but i really hope ubuntu by then has some sort of migration path / upgrade procedure in place, if they're serious about competing with, say, a commercial/proprietary/closed source desktop OS

---

### Post by taurus on 2007-01-03
> **koenn said:**
> 
I know the next LTS release is still 2.5 years from now, but i really hope ubuntu by then has some sort of migration path / upgrade procedure in place, if they're serious about competing with, say, a commercial/proprietary/closed source desktop OS

Maybe there will be one so you have to wait until the next TLS releases to see how you would upgrade from one TLS version the the next!

---

### Post by bodhi.zazen on 2007-01-03
> **koenn said:**
> It's not necessarily that simple, and the original question was a good one. 
Say you're working in an IT department somewhere, maintaining 250 ... 1000 ... ??? .... 

Upgrading that size of an outfit is obviously complicated and not what the OP was asking. With  that size of an organization maintaining all those desktops, let alone upgrading, can be quite a challenge.

Most organizations of that size will have a migration/update plan that likely would not include updating Ubuntu on all those desktops for obvious reasons. IMO they would either continue with what is working or update Ubutnu LTS when hardware is upgraded.

I have never seen an organization of the size you are referring to upgrade so many desktops with any OS, windows or otherwise, without a concurrent hardware upgrade.

There are several options, upgrade 25 % of all boxes every year, or upgrade 100 % every 3-4 years. Pick your poison ....

In most large organizations mission critical data is on a central server(s) and not on desktops. Thus, it is easier to upgrade. You test a new distro, if it is working you update the workstations, wiping hard drives or replacing hardware as needed.

I am not familiar with any IT department that supports/backs up data or user customizations on a personal PC's on the scale of 100's or 1000's of PC's as you suggest and if they do they certainly are not very efficient. In such a case updating to a new version of LTS is the least of their problems ....

---

### Post by koenn on 2007-01-03
> In most large organizations mission critical data is on a central server(s) and not on desktops. Thus, it is easier to upgrade. You test a new distro, if it is working you update the workstations, wiping hard drives or replacing hardware as needed.
That's true, and that's why i did not mention data. I was talking about customized configs.

Wipe the hard disk, (or wait for new hardware), clean install, and reproduce the config in some automated way is one option, one I like actually, and linux hase the tools to make that possible.

Still, there may be scenario's where this is impossible, and usually large outfits prefer standardized desktops, so the os upgrade cycle may not always follow the hardware replacement cycle, and you may want to upgrade because you don't want to support 2 versions, or the older version has become inadequate.
An almost real live example : Dapper does not handle belgian electronic ID cards very well - edgy does, so presumably the nex LTS will too. If being able to use electronic ID cards is important to a company (and it might well be in a couple of years, they'll propably consider upgrading all their desktops.

Telling your coorparate user base to figure out the migration on their own when their LTS has ended might not exactly be the kind of support they expect - is all I wanted to say.

---

### Post by bodhi.zazen on 2007-01-03
> **koenn said:**
> That's true, and that's why i did not mention data. I was talking about customized configs.

Wipe the hard disk, (or wait for new hardware), clean install, and reproduce the config in some automated way is one option, one I like actually, and linux hase the tools to make that possible.

I agree with the automated update/configuration. I also acknowledge the complications of upgrading, that is what planning for upgrades are for. I prefer to upgrade hardware and OS at the same time as well as uniform desktops. It is a hassle to maintain Windows 2000, XP, Vista, and say Ubuntu across an organization.

> Still, there may be scenario's where this is impossible, and usually large outfits prefer standardized desktops, so the os upgrade cycle may not always follow the hardware replacement cycle, and you may want to upgrade because you don't want to support 2 versions, or the older version has become inadequate.

Yes, this is what I am saying also.

> An almost real live example : Dapper does not handle belgian electronic ID cards very well - edgy does, so presumably the nex LTS will too. If being able to use electronic ID cards is important to a company (and it might well be in a couple of years, they'll propably consider upgrading all their desktops.

Telling your coorparate user base to figure out the migration on their own when their LTS has ended might not exactly be the kind of support they expect - is all I wanted to say.

While I agree with the sentiment, what OS provides the support your are asking for? Sign me up that way I can do away with my IT department :p 

Coorparate users of the scale we are discussing employ IT departments or outsource, I know of no OS that provides the kind of maintenance/upgrades you are referring to.

Microsoft certainly leaves the "user base to figure out the migration on their own" so I have to disagree with you there.

---

### Post by koenn on 2007-01-03
> Coorparate users of the scale we are discussing employ IT departments or outsource, I know of no OS that provides the kind of maintenance/upgrades you are referring to.
Microsoft certainly leaves the "user base to figure out the migration on their own" so I have to disagree with you there.
Coorporate users of the scale we're discussing employ IT departments that develop and implement a migration, using documentation and tools provided by th OS vendor. Microsoft does that. They provide install media that can be run to install on blank hard drives as wel as setup.exe's that can be run inside the older version to upgrade to the newer version of the OS. They provide documentation about which older versions can be upgraded to which newer versions. If a direct upgrade from version X to version Z is not possible, but you could migrate by upgrading from X to Y, then modify this or that, then upgrade to Z, they will document that as well. Some times, they provide toolkits such as compatibility testers or "migrate your settings" tools.

It's up to your IT department to study the possibilities, figure out what is are the feasable scenarions in their given situation (your business), make a choice, work out the details, test it,   (start again if the tests aren't succesfull), develop a way to roll it out over all the desktops (as automatically as possible, again using the tools provided); implement it, and provide a rollback plan in case something unecpectedly goes wrong, so you can upgrade without things rbreaking all over the place. (Don't fire them just yet :) )

As Taurus said, we'll probably say how it works in 2 years or so, but as the OP said, given the Dapper to Edgy upgrade experience, I do hope someone will have thought this through by then.

---

### Post by bodhi.zazen on 2007-01-03
LOL :lol:

I was hoping you would provide an OS for me :p

Peace be with you koenn

---

### Post by koenn on 2007-01-03
And with you

---

### Post by az on 2007-01-03
AFAIK, the next LTS version will have a simple upgrade path from the current one. 

The same thing that happened when Dapper was released - in Breezy, you got an update-manager option to upgrade to the next release with one click.  That method provided a lot of tweaks which would fix potential problems which would have resulted in the ubuntu-desktop package getting removed.

That upgrade-manager upgrade path was made for dist-upgrading from one LTS to the next.  When Edgy was released, that option was not show by default, although you could run it by hand.  

Many of the Ubuntu deployments will not use anything but the current LTS.  That would also mean that the next LTS would be released before support for the current one is dropped.

When the next LTS is released depends on the free software world.  For Dapper, a few key upstream projects achieved new stable releases around the same time.  I'm sure the next time that happens, Ubuntu will jump on the opportunity to make another LTS.

If it cannot happen before Dapper's support is scheduled to be dropped, I would assume they would end up extending support.

---

### Post by OrangeCrate on 2007-01-04
> **azz said:**
> AFAIK, the next LTS version will have a simple upgrade path from the current one.
Though bodhi.zazen's solution wasn't ideal, it is certainly doable, and acceptable if need be for a single user. I could live with the loss of customization if I had to, but not data.

Maybe I was not as articulate as I should have been, but I'm sure that everyone figured out, that the loss of customization was the primary issue that prompted the questions regarding the necessity of adopting intermediate upgrades prior to another LTS version being released.

The answer above, is what I was hoping for, and I'm glad that people are thinking about it. For now, I will comfortably continue on my merry way, and use 6.06, unless there's a new "toy" that shows up that I can't live without.

Thanks to all for your input and thoughts. This thread became a lot more interesting than it was originally intended to be...

---

### Post by tszanon on 2007-01-04
I think that it will be easy to release a new update-manager capable of upgrading to the next LTS version directly. Developers probably have already thought about it when they came up with the LTS idea, but haven't done anything yet for an obvious reason: there's not another LTS version yet.

---

