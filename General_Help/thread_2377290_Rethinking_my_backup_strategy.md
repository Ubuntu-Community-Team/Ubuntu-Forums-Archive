---
title: "Rethinking my backup strategy"
date: 2017-11-11
forum: General Help
---

### Post by Adam_Jacobs on 2017-11-11
I've run into a few problems with my backup lately, and I think it might be time for a rethink of my entire strategy.

This is my situation at the moment. This is for home use.

There are 4 computers around the house. The one I use most of the time and which I'm typing this post from uses Ubuntu, and has a whole bunch of general files, photos, emails etc on it. Typical home computer stuff. In total there's a bit under 1TB of data on it. I have another computer connected to my TV running Ubuntu and MythTV, which has a whole load of TV recordings and videos on it. There's well over 2TB of stuff there.

My GF has a Windows computer and a Mac, both of  which she uses for work. She's much more frugal than me and only has a couple of hundred GB of stuff.

At the moment, my backup strategy consists of a combination of Dropbox and some rather elderly NAS drives sitting around the house. The NAS drives get full on a regular basis and I have to figure out what's less important to back up (this is what's made me think it's time for a rethink). All the really important stuff from my own and my GF's computers are stored in Dropbox, and we both have automated scripts that back up a whole lot of other stuff to our elderly cranky NAS drives. All the TV recordings from the MythTV box are not backed up to Dropbox, and are only backed up to the NAS drives.

I'm not thinking of departing radically from this scheme, only tweaking it, but if anyone wants to tell me that there are really much better ways of doing all this stuff these days, then I'm open to suggestions.

Am I right in thinking that Dropbox is pretty safe? Or should I be worried about what happens if I wake up one day and find Dropbox have gone out of business? Is it unwise to rely 100% on Dropbox to keep everything safe?

I'm thinking that I can still back up things to NAS boxes by just buying a bigger and better one. Maybe something like this with some nice big disks to go in it:

[https://www.amazon.co.uk/Synology-DS416SLIM-Bay-Desktop-Enclosure/dp/B01D9YVJ1W/](https://www.amazon.co.uk/Synology-DS416SLIM-Bay-Desktop-Enclosure/dp/B01D9YVJ1W/)

Does that sound reasonable?

This strategy should keep most of the really important stuff safe (assuming that Dropbox is safe), but obviously if something like a fire or a burglary were to hit my computers and my NAS boxes at the same time, then I'd lose all my TV recordings. Not a disaster, but certainly massively annoying. I wonder if there's some sort of online backup service that might be good for that? Would something like Amazon Glacier storage be a good solution given that I'd probably only want to get the stuff back in rather rare circumstances?

Am I thinking along the right lines here, or am I overlooking something obvious?

Thanks
Adam

---

### Post by Tadaen_Sylvermane on 2017-11-11
I think most would agree the safest storage is what you control. Maybe get with a friend and have a server at his /her house and vpn or sync via ssh (if isp speed good enough). Is what i would do.

I keep some stuff on google drive but id rather control it myself for sure.

---

### Post by SeijiSensei on 2017-11-11
I bought this [4GB USB drive]("https://www.newegg.com/Product/Product.aspx?item=N82E16822178741"), reformatted it to ext4, and back up everything to it via rsync.

---

### Post by speartip on 2017-11-12
I have a 1TB external hard drive that I bought from Amazon, & back everything up to that using Areca.
[http://www.areca-backup.org](http://www.areca-backup.org)
I too am a little bit paranoid about backing up sensitive info to Dropbox or Google Drive.

---

