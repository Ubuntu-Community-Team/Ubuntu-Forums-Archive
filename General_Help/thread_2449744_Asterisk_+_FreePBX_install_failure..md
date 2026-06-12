---
title: "Asterisk + FreePBX install failure."
date: 2020-09-01
forum: General Help
---

### Post by syngreis on 2020-09-01
when i run these commands from this guide ([https://computingforgeeks.com/how-to-install-freepbx-15-on-ubuntu-debian-linux/](https://computingforgeeks.com/how-to-install-freepbx-15-on-ubuntu-debian-linux/)) i run into this error.

Command
```

./install -n --dbuser [user] --dbpass [pass]

```

```

root@ubuntu:/usr/src/asterisk-17.6.0/freepbx# sudo ./install -n --dbuser [user] --                                                                                                                                                             dbpass [pass]
Assuming you are Database Root
Checking if SELinux is enabled...Its not (good)!
Reading /etc/asterisk/asterisk.conf...Done
Checking if Asterisk is running and we can talk to it as the 'asterisk' user...Y                                                                                                                                                             es. Determined Asterisk version to be: 17.6.0
Checking if NodeJS is installed and we can get a version from it...Yes. Determin                                                                                                                                                             ed NodeJS version to be: 12.18.3
Preliminary checks done. Starting FreePBX Installation
Checking if this is a new install...No (/etc/freepbx.conf file detected)
Updating tables admin, ampusers, cronmanager, featurecodes, freepbx_log, freepbx                                                                                                                                                             _settings, globals, module_xml, modules, notifications, cron_jobs...Done
Initializing FreePBX Settings
Finished initalizing settings
Copying files (this may take a bit)....
 9363/9363 [============================] 100%
Done
bin is: /var/lib/asterisk/bin
sbin is: /usr/sbin
Finishing up directory processes...Done!
Running variable replacement...Done
Creating missing #include files...Done
Setting up Asterisk Manager Connection...Done
Running through upgrades...
Checking for upgrades..
No further upgrades necessary
Finished upgrades
Setting FreePBX version to 15.0.16.60...Done
Writing out /etc/amportal.conf...Done
Chowning directories...
Taking too long? Customize the chown command, See http://wiki.freepbx.org/displa                                                                                                                                                             y/FOP/FreePBX+Chown+Conf
Setting Permissions...
Setting base permissions...Done
Setting specific permissions...
    0 [>---------------------------]
In Encoding.php line 196:


  Array and string offset access syntax with curly braces is deprecated




chown [-f|--file FILE] [-m|--module MODULE]




In Process.php line 239:


  The command "/usr/sbin/fwconsole chown" failed.


  Exit Code: 255(Unknown error)


  Working directory: /usr/src/asterisk-17.6.0/freepbx


  Output:
  ================




  Error Output:
  ================




install [--dbengine DBENGINE] [--dbname DBNAME] [--dbhost DBHOST] [--cdrdbname C                                                                                                                                                             DRDBNAME] [--dbuser DBUSER] [--dbpass DBPASS] [--user USER] [--group GROUP] [--d                                                                                                                                                             ev-links] [--skip-install] [--webroot WEBROOT] [--astetcdir ASTETCDIR] [--astmod                                                                                                                                                             dir ASTMODDIR] [--astvarlibdir ASTVARLIBDIR] [--astagidir ASTAGIDIR] [--astspool                                                                                                                                                             dir ASTSPOOLDIR] [--astrundir ASTRUNDIR] [--astlogdir ASTLOGDIR] [--ampbin AMPBI                                                                                                                                                             N] [--ampsbin AMPSBIN] [--ampcgibin AMPCGIBIN] [--ampplayback AMPPLAYBACK] [-r|-                                                                                                                                                             -rootdb] [-f|--force]




```

im still learning the ropes oflinux and is currently on ubuntu 20.04.

i dont quite understand the reason of this error as its simply trying to chown a directory. Perhaps someone with more experience with FreePBX could share. i havent found a solution that worked so im hoping on someone can share some insight of the appropriate course of action here.

Also maybe share insight into how to get voip working with actual phone number to incoming. I have no experience and have no clue where to even begin. Eg. somenoe dials 555-1234 and it get routed to my server. How does that infrastructure work?

---

### Post by TheFu on 2020-09-02
> **syngreis said:**
>  
Also maybe share insight into how to get voip working with actual phone number to incoming. I have no experience and have no clue where to even begin. Eg. somenoe dials 555-1234 and it get routed to my server. How does that infrastructure work?

I stopped running my own PBX about 10 yrs ago and just pay a service $5/month instead. That gets me inbound and outbound connectivity to the POTS network, so I don't need a $35/month POTS line to the house and a specialized ATA to connect the SIP PBX to the POTS network.  Because we want to use our normal phones anyways, having a cheap ATA ($35) that the phone system connects into makes that pretty easy. Was using an ht-502 for a long time. When that died after 10+ yrs, had to get a newer ht-702 which has been working well.  I suppose that people use soft-phones instead, but that had a terrible WAF - it wasn't going to happen.  All inbound calls are free. Outbound calls are $0.005 per minute (I think).  We don't worry about it, since we've saved over $30/month from having a regular POTS line for years and years.  I know Android has a SIP client and that it works.  I'll use that when traveling to places with good internet. The last 3 yrs or so, my travels have been to places that have no coverage, no internet, and barely any electricity, so I haven't used it.

Back when I ran my own PBX, I looked at the freePBX distro and at building my own setup with Asterisk, but decided that freeswitch would provide better voice quality (it does). After a few years of maintaining that, I got tired and decided to simplify by using a VoIP service. Never looked back after trying a few services in a few months. Eventually, found a cheap, quality, provider for my area and have been pre-paying for the service ever since.  Basically, they run the freeswitch and I have controls for connectivity from our SIP devices.

SIP security is pretty terrible. A hacked account can be abused by anyone in the world to run up phone bills of $10,000 in a month. This used to be much more common than it is today.  Kids today tend to use whatsapp, skype, or some other voice chat network for most things and use their cell phones for talking with "old people" and legacy businesses that don't support the newer chat tools, banks and insurance companies and many govts.

* POTS - plain old telephone service. I.e. a regular telephone line and number.
* ATA - a device that converts to/from SIP. There are stand-alone ATAs that sit on a network, there are PCIe ATAs.
* FXS or FX0 connects to a POTS line. These can be fussy.

Staying 100% SIP is pretty easy, until you want to call Grandma.

I don't know how to accomplish a POTS connection without a monthly charge.  If you don't pay a service, then you'll need hardware.

That's more than I know about that.
Sorry, I know nothing about the install you are having trouble accomplishing.  Back when I played with this stuff, most people got a full, pre-built distro and installed that for asterisk.

The learning curve for telephony is pretty steep. Trying to get both telephony and Linux skills at the same time sounds really, really, hard.

---

