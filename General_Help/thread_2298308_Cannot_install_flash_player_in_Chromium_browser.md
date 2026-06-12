---
title: "Cannot install flash player in Chromium browser"
date: 2015-10-10
forum: General Help
---

### Post by KayeNg on 2015-10-10
Hi guys.  I DON'T want to use google chrome.  I've followed this procedure but chromium doesn't seem to detect the flash.

o Save the plugin tar.gz locally and note the location the file was saved to.
	o Launch terminal and change directories to the location the file was saved to.
	o Unpack the tar.gz file.  Once unpacked you will see the following:
		+ libflashplayer.so
		+ /usr
	o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
	o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
		+ cp libflashlayer.so <BrowserPluginsLocation>
	o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
		+ sudo cp -r usr/* /usr

Help please

---

### Post by night_sky2 on 2015-10-10
pepperflashplugin-nonfree package no longer works?

---

### Post by coffeecat on 2015-10-10
Support, not a Cafe thread.

*Thread moved to **General Help**.*

You can install the Pepperflash plugin from the Software Centre or Synaptic but it doesn't auto-update. You need to remember to run this terminal command occasionally:

```
sudo update-pepperflashplugin-nonfree --status
```

Which gives me this output at the moment, telling me I am up-to-date:

```
Flash Player version installed on this system  : 19.0.0.185
Flash Player version available on upstream site: 19.0.0.185

```

If it showed a later version available, one would need to run this to update:

```
sudo update-pepperflashplugin-nonfree --install
```

Also - @KayeNg, where did you find those instructions? If on this site, I'll add a health warning.

---

### Post by KayeNg on 2015-10-10
Thanks guys! Those instructions were the readme file that came with the flash download!  Someone also re-posted it in either ubuntuforums or askubuntu, forgot which one, sorry

---

### Post by KayeNg on 2015-10-10
It worked guys, thanks a lot.  I'll mark this thread as closed, but maybe you can help me with this too:

[http://ubuntuforums.org/showthread.php?t=2298310&p=13370714#post13370714](http://ubuntuforums.org/showthread.php?t=2298310&p=13370714#post13370714)

Thank you!

---

### Post by Mike_Walsh on 2015-10-10
If you were seeing 'libflashplayer.so', that's the Linux Flash Player kernel module, which is stuck at 11.2.202.xxx; it's NPAPI (in-process), and is the one that FireFox uses.

To use Flashplayer with Chromium, even though you don't want Chrome, you still must use the same type of Flashplayer that Chrome uses; the 'lib[COLOR=#ff0000]**pep**[/COLOR]flashplayer.so' kernel module, also known as PepperFlash, which is PPAPI, or 'out-of-process'. This is to do, I believe, with the 'sandboxing' that Chrome/Chromium has employed for the last 8 or 9 versions.

It's hardly surprising it needs the same module, since Chrome is based on the Chromium Project; that's where all the cutting edge development work is done. When it's stable, Google take it, add their proprietary 'stuff' to it, and release it badged as 'Chrome'.

I think the last Linux version of Chromium to natively use the Linux Flashplayer was 32, or thereabouts.....


Regards,

Mike. ;)

---

### Post by coffeecat on 2015-10-11
@KayeNg, I've come across something that I missed when it happened earlier this year:

[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

If I'm reading that right, enabling the partner repository and installing the adobe-flashplugin package will keep your pepper flash for Chromium up to date with the usual updates, meaning that you won't have to go through that terminal update-pepperflashplugin-nonfree rigmarole every so often. If I'm wrong, perhaps someone could clarify.

Also - and off-topic to your question - I was hoping that replacing the older flashplugin-installer package with adobe-flashplugin would give me pepperflash in Firefox without the need to add the webupd8 ppa. Seemingly not. I still have the ancient flash version 11.2.202.521 in Firefox.

The above link leads to:

[https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash)

Which is an admirably clear set of instructions but, sadly, doesn't contain the detail to answer the questions I have.

---

### Post by Mike_Walsh on 2015-10-15
Coffeecat, as far as I'm aware ( and I have to confess to being rusty with this now; I spend far more time with my Puppies than I do with Xubuntu these days....aren't I terrible!), this whole business of the different Flash plugins for FireFox and Chrome/Chromium confuses many people.

I know the 'buntu method for obtaining the PPAPI PepperFlash for Chromium involves downloading Chrome, stripping out Pepper, and then discarding the rest.....bit of a waste for those of us with low-ish bandwidth 'caps' imposed by our ISPs. Without looking (I'm not in a position to do so at this moment...I've only got one of my 'Pups' on a flash drive with me currently, running on a mate's desktop), you should find Pepperflash for the Chromium browser somewhere around /usr/lib/chromium (possibly /chromium browser?) /plugins; I haven't had a look around the file-system for a while now.

If you've no objection to doing a manual, hands-on install, we on the Puppy Forums get our Chromium Pepperflash plugin from a guy named 'alienbob', who does quite a bit of playing around with and compiling Slackware-based stuff. By all accounts, he's a somewhat "quirky(!)" individual.....but his software is always **flawless**. Best coding I've seen anywhere. It's available from here:- 

[http://www.slackware.com/~alien/slackbuilds/chromium-pepperflash-plugin/pkg/14.1/](http://www.slackware.com/~alien/slackbuilds/chromium-pepperflash-plugin/pkg/14.1/)

Third item from the bottom. Extract the 'libpepflashplayer' to a 'temporary' directory, then swap it over with your existing one.

It works fine with all the 'buntu-based 'Pups', too.....so I can't see **any** reason why it should give problems in Ubuntu itself; it's only a .so kernel object, after all. I'm going to try it in Xubuntu one of these days, as I always run Chromium by preference...and the system updates seem to lag well behind the current Chromium release schedules. I've been using it, trouble-free, for the last year, so......I'm going to give it a go. I can't see as it'll do anything that can't be put right fairly easily.

As to your other point; as far as I know, you can only use Pepper with FF via the 'pepperflashwrapper' thing.....I think Mozilla themselves offer this as an 'add-on' anyway (although I believe that the Ubuntu version of FF has the normal update mechanism removed by default). Yes, your first link **would** give you Pepper for FF, but only if you've already got the 'pepperflashwrapper' installed first.....which merely allows FF to make use of the plugin that's installed for Chrome/Chromium. I don't think it would automatically allow FF to use it, without this 'adaptive' mechanism being employed.....mostly down to the differences between the way that the FF 'Gecko' and Chromium 'Blink' rendering 'engines' work.

But having read the link, I wasn't aware the old 'nonfree' installation method had changed. News to me, too.

I'm afraid that working with 'Pups' tends to make you happy to try all sorts of workarounds & 'modifications' (read 'hacks'!) that **aren't** strictly in line with Forum policy of doing things according to a time-honoured, accepted 'safe' method.....but I've come across several individuals, recently, who seem to think that **all **Linux users are 'hackers' (and therefore **not** to be trusted) anyway..! :roll::lol:

Worth a try, perhaps? 'You only live once...'


Regards,

Mike. ;)

---

