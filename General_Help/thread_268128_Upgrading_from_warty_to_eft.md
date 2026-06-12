---
title: "Upgrading from warty to eft"
date: 2006-09-29
forum: General Help
---

### Post by lassel on 2006-09-29
Hi,

I have a server that has been running stable since warty 4.10 was the hottest thing out there.

I am thinking that it is getting time to upgrade. I have a TV card in it and I am hoping that maybe 3 versions later mythTV will play nice with me :)

I have tweaked the system some and I am really happy with the way it is set up. So I would be very sorry to have to reinstall the whole thing.

My software raid setup must survive. I have more data that I can possibly backup :S

Which path would you recommend me to take to Edgy Eft?

---

### Post by Old Pink on 2006-09-29
Don't, just yet.

If you need to upgrade, go to Dapper. I wouldn't use Edgy on a server until a month after it's released as stable, let things be discovered and fixed. :) 

You wouldn't want downtime! Either go to Dapper, or wait a while for edgy. :)

---

### Post by lwr on 2006-09-29
I agree completely with Matt.H. If you don't want to have to upgrade again in 18 months, then Dapper is probably the best choice, as it's supported for 5 years I think on servers. Oh, and I've never heard of MythTV playing nice with anyone on any version of any distro (though I might be wrong), so good luck with that.

---

### Post by lassel on 2006-09-30
Oh, I plan on waiting for Eft to get stable.
I only get to tinker with the box a few late hours in the weekends, so if I start thinking about Eft now it will probably be november before I have all the backups in place and are ready to upgrade.

I need to figure out how much preperation I need to do before the actual upgrade.

So the question is **how** to upgrade from warty to eft?

---

### Post by lompolo on 2006-10-05
edit your /etc/apt/sources.list

replace warty words with edgy (or dapper)
apt-get update
apt-get dist-upgrade

edit: Agreed posts below. Incremental upgrades are much safer way.

---

### Post by ciscosurfer on 2006-10-05
@lompolo,
With all due respect, your suggestion to simply change instances of 'warty' and replace with 'edgy' is just asking for trouble!  You should upgrade incrementally!  It is much, much safer (and there is much less risk of breaking your system, etc.) if you update/upgrade version to version.  

@lassel,
If you really want to upgrade to Dapper (which is a good idea), then do it incrementally like I suggest above.  Make the upgrade a smooth transition by upgrading in the following order Warty > Hoary > Breezy > Dapper > Edgy, if you must, but not recommended just yet [this is the order in which the releases came out, and you can do it many ways: by manually changing your sources.list or by using Synaptic or the Update Manager, etc., it's your choice, go with what you're comfortable with)  To do this incrementally, in your sources.list, replace instances of warty with hoary, then update, then dist-upgrade; reboot; replace hoary with breezy, then update, then dist-upgrade; reboot; replace breezy with dapper, then update, then dist-upgade; reboot.  Etc, etc.  Do the same if you want to upgrade to Edgy.  You can also just download a fresh install, backup your data, and then reload your backed-up data to your new fresh install.  I'm of the opinion that it's just easier (and would especially be in your case) to backup your data, download a fresh copy of whichever version you'd like to run (Edgy is still in beta, just remember that...but will soon come out as released version), install the new version and then reinstall your data.  It's much quicker this way.  And yes, there are Server versions available for you!  Good luck!

---

### Post by towsonu2003 on 2006-10-06
upgrade one version at a time. don't jump from warty to edgy, that's not how it's supposed to be done. 

also, for servers, dapper is the better distro to use. edgy is meant to be edge-y, and edgy stuff aren't too stable for servers. hell, if I had a server, I'd run debian stable...

---

