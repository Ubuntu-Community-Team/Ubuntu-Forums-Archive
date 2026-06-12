---
title: "Help writing custom udev rule for Feisty"
date: 2007-09-04
forum: General Help
---

### Post by oscarsfriend on 2007-09-04
Hi,

First thing I have to say here is that I'm not really sure what I'm doing, so I need a little help and patience.

Now, my problem is that my two TV adaptors keep switching places randomly whenever I start up.  One is a Hauppauge Nova-T PCI card, and the other a Freecom DVB-T USB stick.  They should appear as /dev/dvb/adapter0/ and /dev/dvb/adapter1/.  This might not be much of a problem except that if the Freecom stick is first I end up with THREE adaptors (0,1,2) instead of two, for some reason I cannot fathom.  The Freecom stick shows up as 0 and 1, and the Hauppauge as 2, and when this happens it screws up MythTV (and Kaffeine) no end.

OK, so what I want to do is rewrite the udev rule for video devices so as to identify the Hauppauge and Freecom and put them in the order that works (and keep them there).  The rules for doing this appear in /etc/udev/rules.d/20-names.rules, the appropriate section being:

> 
# Video devices, group dvb devices under /dev/dvb
SUBSYSTEM!="dvb", GOTO="dvb_end"
IMPORT{program}="dvb_device_name --export %k"
ENV{DVB_ADAPTER}=="?*", ENV{DVB_DEV}=="?*", \
        NAME="dvb/adapter$env{DVB_ADAPTER}/$env{DVB_NAME}"
LABEL="dvb_end"


So can someone who knows what they are doing help me out here?  I can provide further information to identify the two devices, if someone helps me figure out how to.

Thanks,

Oscarsfriend

---

### Post by kidders on 2007-09-05
Hi there,

> **oscarsfriend said:**
> Now, my problem is that my two TV adaptors keep switching places randomly whenever I start up. This sort of thing is a common enough problem, where naive software forces you to use /dev node names, and then fails to take account of the high likelihood that the names are not static.

> **oscarsfriend said:**
> if the Freecom stick is first I end up with THREE adaptors (0,1,2) instead of two, for some reason I cannot fathom.That's certainly weird. It may be an issue that will go away after your next udev-related system update, perhaps.

In the meantime, your idea about tinkering with udev seems sensible. However, unless you know what you're doing, you should not modify udev rule files you did not create yourself ... that includes opening one & saving it without making any changes. Instead, try creating a ruleset of your own. I would suggest prefixing the name of it with a relatively high number, so it gets processed with a fairly low priority. Off the top of my head, here are a few guidelines to get you started...
[LIST]
[*]Use the "udevinfo" tool to identify something that distinguishes each of the devices you're interested in from the rest of your hardware.
[*]Use that to create a symbolic link in /dev that points to the correct /dev node.
[*]Try to avoid using /dev names that are in any way likely to be needed by your system. Feel free to ask udev to dynamically create new /dev subdirectories ... you might, for instance, decide to create /dev/tvcards/tvcard1, /dev/tvcards/tvcard2, etc.
[*]This way, you can point your apps to your custom symlinks, much as you might do with the contents of /dev/disk/by-label, for example.
[*]The whole thing is a case of trial and error, really. Unfortunately, unlike USB devices, you can't necessarily plug PCI cards in and out at will, so a reboot will be required, any time you tweak your udev ruleset. :-(
[*]Once you're set up, your software should be immune to random device name changes, as well as those that might be caused by things such as future system updates.[/LIST]Hopefully, you can get away with doing things that way. Modifying Ubuntu's own udev rules creates issues that it would be nice not to have to deal with.

Just one additional note: Be sure to "chown root:" and "chmod 644" any new udev rule files you create!

I hope that helps a little.

---

### Post by oscarsfriend on 2007-09-05
Thanks for taking the time to reply.  I *think* I've already fixed the problem, and it now *seems* to work.  It appears that the problem was not due to the devices switching place, but rather the Freecom tuner occasionally (maybe 1 in 10 boots) shows up as two devices, and displaces my second card.  I guess it used to do this before I added the Hauppauge card (on Monday), but I never noticed it when only using the one tuner.

Anyway, here is what I did for anyone with a similar problem.  Please note that this has not yet been tested very well.

Firstly I hacked the /etc/udev/rules.d/20-names.rules and made one minor edit indicated in red the the section quoted below:
```

# Video devices, group dvb devices under /dev/dvb
SUBSYSTEM!="dvb", GOTO="dvb_end"
IMPORT{program}="dvb_device_name --export %k"
ENV{DVB_ADAPTER}=="?*", ENV{DVB_DEV}=="?*", \
        NAME="dvb/[COLOR="Red"]broken/[/COLOR]adapter$env{DVB_ADAPTER}/$env{DVB_NAME}"
LABEL="dvb_end"

```

This shifts all of the dvb devices safely out of the way (I had to do it this way as both MythTV and Kaffeine look for the cards with names of the form /dev/dvb/adapterX).  Next I added the following line to /etc/udev/rules.d/10-local.rules (which I had previously created to create a link to my Hauppauge remote):
```
KERNEL=="dvb0.frontend0",RUN+="/etc/udev/scripts/dvbcorrect"
```
This runs the following script once after creating the devices, that sets up symlinks to the dvb devices in /dev/dvb/broken.  The script is:
```

#!/bin/sh

# Always map Hauppauge to /dev/dvb/adapter1 and Freecom to /dev/dvb/adapter0
# and ignore rogue second Freecom device if present

rm -f /dev/dvb/adapter0 /dev/dvb/adapter1

if [ -d /dev/dvb/broken/adapter2 ];then
  if [ `udevinfo -a -p $(udevinfo -q path -n /dev/dvb/broken/adapter2/frontend0) | grep "ATTRS{vendor}==\"0x14f1\""` ]; then
    ln -s /dev/dvb/broken/adapter0 /dev/dvb/adapter0
    ln -s /dev/dvb/broken/adapter2 /dev/dvb/adapter1
  else
    ln -s /dev/dvb/broken/adapter1 /dev/dvb/adapter0
    ln -s /dev/dvb/broken/adapter0 /dev/dvb/adapter1
  fi
else
  if [ `udevinfo -a -p $(udevinfo -q path -n /dev/dvb/broken/adapter0/frontend0) | grep "ATTRS{vendor}==\"0x14f1\""` ]; then
    ln -s /dev/dvb/broken/adapter0 /dev/dvb/adapter1
    ln -s /dev/dvb/broken/adapter1 /dev/dvb/adapter0
  else
    ln -s /dev/dvb/broken/adapter0 /dev/dvb/adapter0
    ln -s /dev/dvb/broken/adapter1 /dev/dvb/adapter1
  fi
fi

```

Note that the two Freecom devices always seem to show up in pairs so this should cover every eventuality.

This info might also be useful to someone who has two or more dvb cards that they need to keep static -- e.g. a cable and a terrestrial card -- so that it doesn't cause all sorts of problems with MythTV.  Of course they will need to tailor the final script to suit their set up.

Thanks again for taking the time to respond though, kidders.

---

### Post by oscarsfriend on 2007-09-06
Hi,

My problem is still happening!  I don't think that the rogue freecom device is caused by udev.  My script ran during boot as it should and made links, but to the two freecom devices.    When I restart udev manually all seems to work fine.  The only way I can see this happening is if the extra device is created later in the boot sequence. 

EDIT: It could be that my script is being run too early.  Maybe I should use a higher number for the udev rule file?

EDIT2: I was right.  I created another script that began 98 (instead of 10), which seems to have solved the problem.

---

