---
title: "TIPS: Synce, PPC, WM6, sync evolution with smartphone in Gnome"
date: 2008-03-07
forum: General Help
---

### Post by prostar on 2008-03-07
Since I just went through a week long process to get this working, I thought that I would post my findings in hopes that others may save an hour or two.  All I wanted to do was sync my HTC Hermes with Evolution.  Little did I know that was no small feat.  It seemed quite easy to browse files, get status,view installed apps, and even use nautalis, but syncing was a HNL.

Here is a breakdown of potential pitfalls.

[LIST]
[*]The synce Wiki is useless
[*]Posts here in the forum are old and point to old solutions
[*]To accomplish this you have to get 3 components to work together and none of them tell you if they can talk to each other or not.
[*]Following an old post that added to the repositories resulted in multiple copies of stuff and I didn't know which one to go with
[*]The copy of sync-engine in the repositories doesn't work as far as Synce is concerned
[*]After getting the SVN copy of sync-engine the "install-plugins.py" script detected the right version of opensync (0.22) but installed the .3x plugin anyway.
[*]Somewhere in all that info I found the statement that "odccm" is outdated and won't work, use vdccm.  I found this to be a red herring and vdccm caused me way more problems.
[/LIST]

In the end here is the setup I have which is working.
(search for 'synce')
librtfcomp0 - Library to read compressed RTF files
libsynce0 - Helper library for SynCE, a tool to sync Windows Mobile devices
odccm - Daemon to keep a connection to Windows Mobile device
python-rtfcomp - Library to read compressed RTF files (python bindings)
synce-gnomevfs - SynCE plugin for Gnome VFS
synce-serial - SynCE connection manipulation scripts
usb-rndis-modules-2.6.22-14-generic - usb-rndis modules for Linux (kernel 2.6.22-14-generic).
usb-rndis-source - Source for the usb-rndis driver

(search for 'opensync', these are all version:0.22feisty2)
libopensync0 - Synchronisation framework for email/pdas/and more
libopensync-plugin-evolution2 - Evolution plugin for opensync
libopensync-plugin-python - Python engine for OpenSync
multisync-gui - GTK Gui interface for OpenSync
multisync-tools - PIM Synchronization Command Line Tools
opensyncutils - Command line utilities for libopensync
python-opensync - Python bindings to the opensync synchronisation engine

After all those are installed use (find thread) thread to get the svn 'sync-engine'.  MANUALLY copy the file ....plugin-2x.py to the usr/lib/plugins (or /usr/lib/python/plugins?) and rename (or link) it as "synce-plugin.py".

Make sure that it is recognized as "synce-opensync-plugin" and not just "synce-plugin".
```
msynctool --listplugins
```

There are other threads that show you how to get the RNDIS working if it didn't work out of the box.  I found the 'synce-trayicon' handy but not necessary.

Here's how I started things:
[LIST]
[*]start "sudo odccm &"
[*]Start "/svnpath/sync-engine/sync-engine" in it's own window
[*]Start "synce-gnome &"
[COLOR="Red"][*]Start "sudo synce-serial-start"[/COLOR]  *** Not needed for newer phones
[*]Wait for pop-up from synce-gnome to say connected (maybe unplug/plug device)
[*]use msynctool or multisync-gui to sync device
[/LIST]

[COLOR="Red"]*** It turns out I had enabled "legacy" support in all my efforts to get this working.  This meant I had turned OFF "Enable advanced network functions" on my WM6 phone.[/COLOR]

I found I had to use the scripts from the sync-engine/tools folder to make a partnership.  I made a few and couldn't get it to work, and couldn't remove them with the scripts.  I had to use the phones ActiveSync (while not connected) to remove the extra "sources".  Also I found that I had to initiate the sync from the phone the first time.  I guess this is because the "set_active_partnership.py" script was missing from my tools folder?

As far as disconnecting or starting things automatically?   I haven't got that far, but it shouldn't be too bad.

---

### Post by mrund on 2008-03-09
Oh man, what a mess. Your entry told me exactly what I needed to know: SynCE is a ******* to install, doesn't have a GUI and isn't ready for prime time.

So I'm thinking that the best way to get mp3s onto my handheld is probably to get a MiniSD dongle with a USB plug and hope it'll play nice with Ubuntu. Or simply transfer them from the Win machine I have at work.

---

### Post by prostar on 2008-03-12
For MP3 it's easy, easy.  No need to go through all the setup with Synce.  I had file transfer and program install working in no time.  It's Calendar, Contact, Note, etc. syncing that's a beast.  Install synce-gnome-vfs or whatever it's called and you can browse files with Nautalis.  Also they just updated the opensync component to 0.11 (was 0.10).

---

### Post by Trab on 2008-04-07
> **mrund said:**
> Oh man, what a mess. Your entry told me exactly what I needed to know: SynCE is a ******* to install, doesn't have a GUI and isn't ready for prime time.

So I'm thinking that the best way to get mp3s onto my handheld is probably to get a MiniSD dongle with a USB plug and hope it'll play nice with Ubuntu. Or simply transfer them from the Win machine I have at work.

I wrote the original Synce howto that worked for a while, so I've had my share of experience with synce.

I agree whole heartedly with your post, as its exactly what I did. I got a SD card and reader, and put all my music on it. worked without a hitch.

---

### Post by VeeDubb on 2008-04-11
If anybody missed the news, the newest version of Manriva Linux, 2008-Spring, has EXCELENT support for Windows Mobile devices.  You just install a meta-package called task-WM5sync-kde or task-WM5sync-gnome and it will install and configure everything you need to sync.  

The only thing you need to do is run the program synce-kpm once to creat the partnership and it's all automatice from them on.  It uses kitchensync as a front end in kde, and multisync as the front end for gnome.

---

### Post by edmcdonagh on 2008-04-17
Do these instructions change at all for Hardy Beta?

---

### Post by beefcurry on 2008-04-18
Glad someone tried to sync the HTC Hermes, its something I tried a year ago and gave up mid way... 

Looks like you really had determination :D. Since the Keyboard of my HTC Hermes no longer works I will likely replace it soon, or fix it. Untill I do that I'll just make do without syncing, like I've done for the past year.

---

### Post by abhilashkumar on 2008-05-01
librtfcomp0
odccm
python-rtfcomp

and a few others are not found in the repositories.
Do I have to add a new source.

I am running Hardy 32bit on acer 4520 laptop

---

### Post by Stefanie on 2008-05-01
it didn't work for me :-( sync-engine hangs on "debug sync-engine: installing signal handlers" and aborts after a while. the command synce-gnome is not recognized. 
i really don't know what to do next. SynCE is indeed a real pain. i've heard about those mandriva packages, too. can't they be used on ubuntu?

---

### Post by hosammy on 2008-05-02
> **prostar said:**
> 
In the end here is the setup I have which is working.
(search for 'synce')
librtfcomp0 - Library to read compressed RTF files
libsynce0 - Helper library for SynCE, a tool to sync Windows Mobile devices
odccm - Daemon to keep a connection to Windows Mobile device
python-rtfcomp - Library to read compressed RTF files (python bindings)
synce-gnomevfs - SynCE plugin for Gnome VFS
synce-serial - SynCE connection manipulation scripts
usb-rndis-modules-2.6.22-14-generic - usb-rndis modules for Linux (kernel 2.6.22-14-generic).
usb-rndis-source - Source for the usb-rndis driver

(search for 'opensync', these are all version:0.22feisty2)
libopensync0 - Synchronisation framework for email/pdas/and more
libopensync-plugin-evolution2 - Evolution plugin for opensync
libopensync-plugin-python - Python engine for OpenSync
multisync-gui - GTK Gui interface for OpenSync
multisync-tools - PIM Synchronization Command Line Tools
opensyncutils - Command line utilities for libopensync
python-opensync - Python bindings to the opensync synchronisation engine



Only the followings can be found & installed in ubuntu 8.04 LTS i386 synaptic package:
libsynce0 
synce-serial 
libopensync0
multisync-tools
opensyncutils
python-opensync 

I found the "libopensync-plugin-evolution" instead of "libopensync-plugin-evolution2", is it the same?

What other packages need to be installed in 8.04 LTS version?

:confused:

---

### Post by hosammy on 2008-05-02
I went to the synce web and edited my sources list at:
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)
and can install the followings:
odccm
python-rtfcomp 
synce-gnomevfs 
usb-rndis-modules-2.6.22-14-generic
usb-rndis-source

However, I still cannot install by entering the following command:
sudo apt-get install libopensync-plugin-evolution2 libopensync-plugin-python msynctool

which replied that the packages cannot be found.

---

### Post by Hooya on 2008-05-08
I followed the instructions at that site ([http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)) to the letter and now have my contacts, calendar and tasks syncing between Windows Mobile 6 and Evolution in Hardy x64.

You really have to follow those instructions to the letter though.

Go from the beginning, making sure you take all the extra steps (I had to download that config.xml file in the SynCE page, for instance) if you run into a snag.

The only thing I think is optional is the SynceGnome section.  I don't see what that's doing, but I'm just going to leave it be because I know it can work.

Also, realize that you're going to need two terminals open to do a lot of the stuff here, including just a sync.  One to open the service and the other to do other things with it, like create the partnership and sync with it.  But it can be done.  I've been using Ubuntu for less than a month and I got it working, I'm sure other users can too.  I'm no computer noob, but I am still a *nix noob, so it is a long and complex process, but it's not too hard.  Just be careful to do everything in the wiki.

Sorry that's not being too helpful, but just know that it can be done if you're careful about it.

---

### Post by edkmho on 2008-05-09
Hooya,

I have follow every words in the SynCE Wiki and arrived at the point of creating the partnership, unfortunately i could not create the partnerships. The error is as follow: bash: create_partnerships.py: command not found. 

Would any be able to lend a helping hand in this matter. I am stuck at this point in time. 
Thanks in advance.

After trying several time, finally i managed to create the partnerships and now i am testing it. 

Thanks, guys.

---

### Post by hosammy on 2008-05-09
> **Hooya said:**
> I followed the instructions at that site ([http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)) to the letter and now have my contacts, calendar and tasks syncing between Windows Mobile 6 and Evolution in Hardy x64.

You really have to follow those instructions to the letter though.

I was stuck at here:
Create a partnership

Now we have the sync-engine running you can create a partnership between device and computer by typing in another terminal:

$ create_partnership.py "Linux desktop" "Contacts,Calendar"


The 1st terminal response is:[COLOR="Red"]
sammy@sammy-desktop:~$ sync-engine
SynCE sync-engine starting up
2008-05-09 18:46:51,718 DEBUG syncengine : running main loop
2008-05-09 18:46:51,722 DEBUG syncengine : creating SyncEngine object
2008-05-09 18:46:51,744 INFO engine.syncengine.kernel : __init__: connected device found
2008-05-09 18:46:51,744 INFO engine.syncengine.kernel : _CBDeviceConnected: device connected at path /org/synce/odccm/Device/_610495B4_B684_6613_E99D_18E3622E00D4_
2008-05-09 18:46:51,762 INFO engine.syncengine.kernel :  device Sammy-LG-KS20 connected
2008-05-09 18:46:51,765 INFO engine.syncengine.kernel : ProcessAuth : processing authorization for device 'Sammy-LG-KS20'
2008-05-09 18:46:51,774 INFO engine.syncengine.kernel : ProcessAuth: authorization not required for device 'Sammy-LG-KS20'
2008-05-09 18:46:51,774 DEBUG engine.syncengine.kernel : OnConnect: setting up RAPI session
** Message: Hal reports no devices connected
2008-05-09 18:46:51,824 DEBUG engine.syncengine.kernel : OnConnect: Attempting to bind partnerships
2008-05-09 18:46:51,824 INFO engine.partnerships.Partnerships : AttemptToBind: Reading partnerships and looking for host binding
2008-05-09 18:46:51,824 INFO engine.partnerships.Partnerships : ClearDevicePartnerships: clearing all device partnership info
2008-05-09 18:46:51,824 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: reading partnerships from device registry
2008-05-09 18:46:51,866 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: read partnership ID = 1347574391, Hostname = LIVINGROOM
2008-05-09 18:46:51,867 DEBUG engine.partnerships.Partnerships : _read_device: Adding entry
2008-05-09 18:46:51,891 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: read partnership ID = 373970210, Hostname = SAMMYHO
2008-05-09 18:46:51,892 DEBUG engine.partnerships.Partnerships : _read_device: Adding entry
2008-05-09 18:46:51,916 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: querying synchronization source information from device
2008-05-09 18:46:51,917 DEBUG engine.xmlutil : _config_query: CeProcessConfig request is 
<wap-provisioningdoc>
  <characteristic type="Sync">
    <characteristic-query recursive="false" type="Sources"/>
  </characteristic>
</wap-provisioningdoc>
2008-05-09 18:46:52,694 DEBUG engine.xmlutil : _config_query: CeProcessConfig response is 
<?xml version="1.0" encoding="utf-8"?>
<wap-provisioningdoc>
  <characteristic type="Sync">
    <characteristic recursive="false" type="Sources">
      <characteristic type="{99C33852-3163-40C4-8A00-5E77D040F693}"/>
      <characteristic type="{4E20A7EB-3357-4DDB-BAD8-677394ABEE0E}"/>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>

2008-05-09 18:46:52,695 DEBUG engine.xmlutil : _config_query: CeProcessConfig request is 
<wap-provisioningdoc>
  <characteristic type="Sync">
    <characteristic type="Sources">
      <characteristic-query type="{99C33852-3163-40C4-8A00-5E77D040F693}"/>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
2008-05-09 18:46:53,832 DEBUG engine.xmlutil : _config_query: CeProcessConfig response is 
<?xml version="1.0" encoding="utf-8"?>
<wap-provisioningdoc>
  <characteristic type="Sync">
    <characteristic type="Sources">
      <characteristic type="{99C33852-3163-40C4-8A00-5E77D040F693}">
        <characteristic type="Engines">
          <characteristic type="{176F4FFD-F20C-4BD4-BDD7-01D0726C567B}">
            <characteristic type="CarrierConnectorList"/>
            <characteristic type="Providers">
              <characteristic type="{ED346DE9-375B-3274-DEAF-7D4C7EDAED1B}">
                <parm name="Enabled" value="0"/>
                <parm name="Name" value="Media"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{B7B6ACB2-AF1D-43F5-BF9A-586111B263EF}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#622;"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{7E29B5F7-C686-4B0C-9892-FD8BAD8E0D08}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#1706;&#823;R"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{8E98CB51-85A4-4777-8DEB-A0298DF8899F}">
                <parm name="Enabled" value="0"/>
                <parm name="Name" value="O"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{4A5D9FE0-F139-4A63-A5A4-4F31CEEA02AD}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#34892;&#20107;&#26310;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
              <characteristic type="{0DD8685C-E272-4FCB-9ECF-2EAD7EA2497B}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#36899;&#32097;&#20154;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
              <characteristic type="{783AE4F6-4C12-4423-8270-66361260D4F1}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#24037;&#20316;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
              <characteristic type="{C6D47067-6E92-480E-B0FC-4BA82182FAC7}">
                <parm name="Enabled" value="0"/>
                <parm name="Name" value="&#38651;&#23376;&#37109;&#20214;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
            </characteristic>
            <characteristic type="Settings">
              <parm name="CarrierConnector" value=""/>
              <parm name="ClientNegotiated" value="1"/>
              <parm name="ClientProtocolVersion" value="12.0"/>
              <parm name="ConflictResolution" value="1"/>
              <parm name="DeviceAddressingMethod" value="0"/>
              <parm name="DevicePhoneNumber" value=""/>
              <parm name="DeviceSMSAddress" value=""/>
              <parm name="Domain" value="DEFAULT"/>
              <parm name="EmailAddress" value=""/>
              <parm name="Logging" value="0"/>
              <parm name="NotificationsSupported" value="0"/>
              <parm name="RefreshCertAuthXml" value="0"/>
              <parm name="SavePassword" value="1"/>
              <parm name="ServerAutdSupport" value="0"/>
              <parm name="ServerCertAuthRequired" value="0"/>
              <parm name="ServerHTMLMailSupport" value="1"/>
              <parm name="URI" value="Microsoft-Server-ActiveSync"/>
              <parm name="UseSSL" value="0"/>
              <parm name="User" value="DEFAULT"/>
            </characteristic>
          </characteristic>
        </characteristic>
        <parm name="Name" value="Windows PC 2"/>
        <parm name="Server" value="SAMMYHO"/>
        <parm name="StoreType" value="2"/>
      </characteristic>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>

2008-05-09 18:46:53,949 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: read source GUID = {99C33852-3163-40C4-8A00-5E77D040F693}, Hostname = SAMMYHO, Description = Windows PC 2
2008-05-09 18:46:53,954 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: source matches partnerhip from registry.  Initializing partnership
2008-05-09 18:46:53,956 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: querying partnerhip synchronization items (providers)
2008-05-09 18:46:53,957 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#622;
2008-05-09 18:46:53,958 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:53,958 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 4
2008-05-09 18:46:53,966 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#34892;&#20107;&#26310;
2008-05-09 18:46:53,966 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:53,967 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 0
2008-05-09 18:46:53,967 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#24037;&#20316;
2008-05-09 18:46:53,967 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:53,967 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 7
2008-05-09 18:46:53,968 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider O
2008-05-09 18:46:53,968 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#38651;&#23376;&#37109;&#20214;
2008-05-09 18:46:53,968 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider Media
2008-05-09 18:46:53,968 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#36899;&#32097;&#20154;
2008-05-09 18:46:53,969 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:53,976 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 1
2008-05-09 18:46:53,998 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#1706;&#823;R
2008-05-09 18:46:53,998 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:53,998 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 3
2008-05-09 18:46:53,999 DEBUG engine.xmlutil : _config_query: CeProcessConfig request is 
<wap-provisioningdoc>
  <characteristic type="Sync">
    <characteristic type="Sources">
      <characteristic-query type="{4E20A7EB-3357-4DDB-BAD8-677394ABEE0E}"/>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
2008-05-09 18:46:54,678 DEBUG engine.xmlutil : _config_query: CeProcessConfig response is 
<?xml version="1.0" encoding="utf-8"?>
<wap-provisioningdoc>
  <characteristic type="Sync">
    <characteristic type="Sources">
      <characteristic type="{4E20A7EB-3357-4DDB-BAD8-677394ABEE0E}">
        <characteristic type="Engines">
          <characteristic type="{176F4FFD-F20C-4BD4-BDD7-01D0726C567B}">
            <characteristic type="CarrierConnectorList"/>
            <characteristic type="Providers">
              <characteristic type="{4165683D-D6D2-2B95-47CC-EC3E798234A6}">
                <parm name="Enabled" value="0"/>
                <parm name="Name" value="Media"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{B7B6ACB2-AF1D-43F5-BF9A-586111B263EF}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#622;"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{7E29B5F7-C686-4B0C-9892-FD8BAD8E0D08}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#1706;&#823;R"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{8E98CB51-85A4-4777-8DEB-A0298DF8899F}">
                <parm name="Enabled" value="0"/>
                <parm name="Name" value="O"/>
                <parm name="ReadOnly" value="1"/>
              </characteristic>
              <characteristic type="{4A5D9FE0-F139-4A63-A5A4-4F31CEEA02AD}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#34892;&#20107;&#26310;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
              <characteristic type="{0DD8685C-E272-4FCB-9ECF-2EAD7EA2497B}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#36899;&#32097;&#20154;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
              <characteristic type="{783AE4F6-4C12-4423-8270-66361260D4F1}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#24037;&#20316;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
              <characteristic type="{C6D47067-6E92-480E-B0FC-4BA82182FAC7}">
                <parm name="Enabled" value="1"/>
                <parm name="Name" value="&#38651;&#23376;&#37109;&#20214;"/>
                <parm name="ReadOnly" value="0"/>
              </characteristic>
            </characteristic>
            <characteristic type="Settings">
              <parm name="CarrierConnector" value=""/>
              <parm name="ClientNegotiated" value="1"/>
              <parm name="ClientProtocolVersion" value="12.0"/>
              <parm name="ConflictResolution" value="1"/>
              <parm name="DeviceAddressingMethod" value="0"/>
              <parm name="DevicePhoneNumber" value=""/>
              <parm name="DeviceSMSAddress" value=""/>
              <parm name="Domain" value="DEFAULT"/>
              <parm name="EmailAddress" value=""/>
              <parm name="Logging" value="0"/>
              <parm name="NotificationsSupported" value="0"/>
              <parm name="RefreshCertAuthXml" value="0"/>
              <parm name="SavePassword" value="1"/>
              <parm name="ServerAutdSupport" value="0"/>
              <parm name="ServerCertAuthRequired" value="0"/>
              <parm name="ServerHTMLMailSupport" value="1"/>
              <parm name="URI" value="Microsoft-Server-ActiveSync"/>
              <parm name="UseSSL" value="0"/>
              <parm name="User" value="DEFAULT"/>
            </characteristic>
          </characteristic>
        </characteristic>
        <parm name="Name" value="Windows PC"/>
        <parm name="Server" value="LIVINGROOM"/>
        <parm name="StoreType" value="2"/>
      </characteristic>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>

2008-05-09 18:46:54,793 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: read source GUID = {4E20A7EB-3357-4DDB-BAD8-677394ABEE0E}, Hostname = LIVINGROOM, Description = Windows PC
2008-05-09 18:46:54,802 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: source matches partnerhip from registry.  Initializing partnership
2008-05-09 18:46:54,803 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: querying partnerhip synchronization items (providers)
2008-05-09 18:46:54,804 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider Media
2008-05-09 18:46:54,807 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#34892;&#20107;&#26310;
2008-05-09 18:46:54,808 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:54,808 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 0
2008-05-09 18:46:54,808 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#622;
2008-05-09 18:46:54,809 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:54,809 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 4
2008-05-09 18:46:54,809 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#24037;&#20316;
2008-05-09 18:46:54,810 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:54,810 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 7
2008-05-09 18:46:54,810 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider O
2008-05-09 18:46:54,810 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#38651;&#23376;&#37109;&#20214;
2008-05-09 18:46:54,818 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:54,819 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 2
2008-05-09 18:46:54,819 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#36899;&#32097;&#20154;
2008-05-09 18:46:54,819 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:54,820 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 1
2008-05-09 18:46:54,820 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: found provider &#1706;&#823;R
2008-05-09 18:46:54,820 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider is enabled
2008-05-09 18:46:54,820 DEBUG engine.partnerships.Partnerships : ReadDevicePartnerships: provider ID is 3
2008-05-09 18:46:54,846 DEBUG engine.partnerships.Partnerships : AttemptToBind: No valid host bindings found for any device partnership
2008-05-09 18:46:54,846 DEBUG engine.partnerships.Partnerships : AttemptToBind: setting current partnership to None
2008-05-09 18:46:54,869 DEBUG engine.syncengine.kernel : OnConnect: No valid partnership bindings are available, please create one (org.synce.SyncEngine.Error.NoBoundPartnership: )
2008-05-09 18:46:54,869 DEBUG syncengine : installing signal handlers
[/COLOR]

And the 2nd terminal is:
[COLOR="Blue"]sammy@sammy-desktop:~$ create_partnership.py "sammy" "Contacts,Calendar"Creating partnership...

error: failed to create partnership
error: org.synce.SyncEngine.Error.NoFreeSlots
sammy@sammy-desktop:~$ 
[/COLOR]

I am using Ubuntu 8.04 LTS, 
my mobile phone :
Brand: LG
Model: KS-20
OS: Windows Mobile 6.0

Please advise ...
:confused:

---

### Post by AdamWill on 2008-05-09
Your phone already has two partnerships set up. Windows Mobile can only support two sync partnerships at a time. You'll have to remove one of the existing ones.

---

### Post by Hooya on 2008-05-10
Make sure you always wait for the first terminal to get to the "installing signal handlers" line before running the commands in the second terminal.  The second terminal will go back to a bash when it's done, but the first terminal will never return to a bash, so just close that terminal.  AdamWill is probably right about the partnership issue being on the device side, not the computer side of things.

---

### Post by Stefanie on 2008-05-11
i finally got things working, but there's a problem... i synced my phone's entries to evolution so now i have my calendar in evolution. when i add a new calendar entry in evolution, however, i can't sync this to my phone. how does this work?

---

### Post by AdamWill on 2008-05-12
It should automatically work in both directions. If it doesn't, try just poking around: remove your partnership, re-add it, stuff like that. I've had it fail to sync in one direction on occasion and then when I've messed around a bit more for whatever reason, it starts working again. opensync is a bit temperamental.

---

### Post by scrooge_74 on 2008-06-18
What kind of extra messing around did you do? I am almost there but when I synce my HTC touch it erase any contacts and appointments on the phone

EDIT: It works!!!!

I can sync my HTC touch with my evolution, now if they would only make a linux version for my phone :D I would be in heaven

---

### Post by fwaokda on 2008-07-22
> **scrooge_74 said:**
> What kind of extra messing around did you do? I am almost there but when I synce my HTC touch it erase any contacts and appointments on the phone

EDIT: It works!!!!

I can sync my HTC touch with my evolution, now if they would only make a linux version for my phone :D I would be in heaven

How did you get it to work it isn't working for me I'm stuck at the step where you type this..

synce-pls

---

### Post by dime2007 on 2008-07-22
This worked for me. What should also be noted is that once everything has been done the only action needed each time is the msynctool --sync synce-sync line. 

Now can sometell me how to get that to run when I plug my phone in?

Thanks.

D/

---

### Post by dime2007 on 2008-07-22
> **dime2007 said:**
> 
only action needed each time is the msynctool --sync synce-sync line. 


Or not. Just came back to update stuff on the phone and it needed synce-sync-engine aswell.

Bummer.

D.

---

