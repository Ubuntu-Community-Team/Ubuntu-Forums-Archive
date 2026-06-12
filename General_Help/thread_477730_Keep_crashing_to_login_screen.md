---
title: "Keep crashing to login screen"
date: 2007-06-18
forum: General Help
---

### Post by toecutter on 2007-06-18
Pretty much the entire time I'm sitting at my machine, I'm using Firefox, but lately I get random crashes to the login screen. I used to think it was because I was opening and closing tabs (I use Google Reader every day so there's a lot of that as I read through Digg posts, etc.) so I tried opening fewer tabs. Still crashed. I tried turning off all my add-ons. Still crashed. Then I tried not opening or closing any tabs for a while and it still crashed. This is basically happening 2-3 times per session, and my sessions aren't that long, maybe 2-3 hours or less. 

Very annoying! And no way to be using the computer. I'm on 7.04, these are my Firefox details in case it helps: 
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)

I didn't load anything major on the system last week, I'm still pussyfooting around Ubuntu as I experiment with things so I don't want to jump feetfirst into some new funky thing. I just want to do DVD backups, web surfing, a bit of gaming, that's it...so I'm not the uber-experimental type :)

Any help would be very appreciated!

---

### Post by Gagle on 2007-06-18
I'm not sure I understood properly.  Does your system crash while you're using Firefox or at login ?

regards,

Gagle

---

### Post by toecutter on 2007-06-18
Sorry :) it crashes to the login screen when I'm using Firefox.

I'm on the machine right now but careful not to tax Firefox very much, just in case too much 'stuff' going on might make it crash.

---

### Post by Crafty Kisses on 2007-06-18
> **toecutter said:**
> Sorry :) it crashes to the login screen when I'm using Firefox.

I'm on the machine right now but careful not to tax Firefox very much, just in case too much 'stuff' going on might make it crash.

This could actually be a resource issue, you can view your processes by going into terminal and typing:
```
top
```
That should tell you what's running, at the time of the crash.

If your CPU usage is at 99% for some odd reason and you open Firefox will crash.

Hope this helps.

---

### Post by toecutter on 2007-06-18
Thanks for that, I've got console open now and nothing strange is popping up or showing '99%' except what I assume is the 'idle' note ('99% id').

I've got a pretty strong system apart from just 1gb of ram so I wouldn't expect the system itself to complain, my initial thought is that this is Firefox doing this. 

I'm wondering if I should see if this happens with 32-bit Firefox but I had full system crashes (shutdowns) with Swiftfox and Firefox 32-bit when I was running Edgy and I'd hoped that running Feisty on a fresh install (new HD even) would have 'cured' the problem. 

Is there any way to note what happened BEFORE a crash, as I suspect this command won't tell me that?

---

### Post by toecutter on 2007-06-18
Grrr...

it just happened AGAIN

i was even looking at the 'top' screen in console as it happened! 

'top' was saying that the CPU was 26% (approximately) in use, with '470m' for 'firefox.bin' in the 'VIRT' column.

tried System Log and got this in 'syslog':
- this is from a crash earlier today
Jun 18 19:59:27 frank-linux gconfd (frank-7260): Received signal 15, shutting down cleanly
Jun 18 19:59:28 frank-linux gconfd (frank-7260): Exiting
Jun 18 19:59:28 frank-linux gdm[7194]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

- from the crash just now
Jun 18 21:54:48 frank-linux gconfd (frank-10158): Received signal 15, shutting down cleanly
Jun 18 21:54:48 frank-linux gconfd (frank-10158): Exiting
Jun 18 21:54:48 frank-linux gdm[10092]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

and in 'kern.log':
Jun 18 00:11:08 frank-linux kernel: [ 1856.438873] Bad page state in process 'firefox-bin'
Jun 18 00:11:08 frank-linux kernel: [ 1856.438874] page:ffff81003fe899b0 flags:0x0100000000000000 mapping:0000000000000000 mapcount:0 count:1
Jun 18 00:11:08 frank-linux kernel: [ 1856.438876] Trying to fix it up, but a reboot is needed
Jun 18 00:11:08 frank-linux kernel: [ 1856.438877] Backtrace:
Jun 18 00:11:08 frank-linux kernel: [ 1856.438880] 
Jun 18 00:11:08 frank-linux kernel: [ 1856.438881] Call Trace:
Jun 18 00:11:08 frank-linux kernel: [ 1856.438885]  [__switch_to+646/688] __switch_to+0x286/0x2b0
Jun 18 00:11:08 frank-linux kernel: [ 1856.438892]  [bad_page+88/144] bad_page+0x58/0x90
Jun 18 00:11:08 frank-linux kernel: [ 1856.438904]  [get_page_from_freelist+832/1392] get_page_from_freelist+0x340/0x570
Jun 18 00:11:08 frank-linux kernel: [ 1856.438916]  [__alloc_pages+99/784] __alloc_pages+0x63/0x310
Jun 18 00:11:08 frank-linux kernel: [ 1856.438926]  [copy_strings+190/544] copy_strings+0xbe/0x220
Jun 18 00:11:08 frank-linux kernel: [ 1856.438935]  [copy_strings_kernel+33/64] copy_strings_kernel+0x21/0x40
Jun 18 00:11:08 frank-linux kernel: [ 1856.438939]  [do_execve+335/624] do_execve+0x14f/0x270
Jun 18 00:11:08 frank-linux kernel: [ 1856.438946]  [sys_execve+68/176] sys_execve+0x44/0xb0
Jun 18 00:11:08 frank-linux kernel: [ 1856.438951]  [stub_execve+103/176] stub_execve+0x67/0xb0
Jun 18 00:11:08 frank-linux kernel: [ 1856.438963] 
Jun 18 00:48:24 frank-linux kernel: [ 2803.775051] usb 2-1: USB disconnect, address 4
Jun 18 00:48:24 frank-linux kernel: [ 2803.821623] usb 2-1: new full speed USB device using uhci_hcd and address 5
Jun 18 00:48:25 frank-linux kernel: [ 2803.892239] usb 2-1: configuration #1 chosen from 1 choice
Jun 18 00:48:25 frank-linux kernel: [ 2803.894720] hub 2-1:1.0: USB hub found
Jun 18 00:48:25 frank-linux kernel: [ 2803.895518] hub 2-1:1.0: 2 ports detected
Jun 18 01:53:55 frank-linux kernel: [ 4439.655348] usb 2-1: USB disconnect, address 5
Jun 18 01:53:55 frank-linux kernel: [ 4439.703599] usb 2-1: new full speed USB device using uhci_hcd and address 6
Jun 18 01:53:55 frank-linux kernel: [ 4439.774122] usb 2-1: configuration #1 chosen from 1 choice
Jun 18 01:53:55 frank-linux kernel: [ 4439.776601] hub 2-1:1.0: USB hub found
Jun 18 01:53:55 frank-linux kernel: [ 4439.777399] hub 2-1:1.0: 2 ports detected
Jun 18 07:06:01 frank-linux kernel: [12262.181376] gnome-video-thu[20171]: segfault at 0000000000000010 rip 00002b3162d9eb40 rsp 00007fff4d289ae8 error 4
Jun 18 07:16:26 frank-linux kernel: [12602.472700] warning: many lost ticks.
Jun 18 07:16:26 frank-linux kernel: [12602.472702] Your time source seems to be instable or some driver is hogging interupts
Jun 18 07:16:26 frank-linux kernel: [12602.472708] rip __do_softirq+0x54/0xd0

wth? those timesin kern.log don't match the system time *at all*

can anyone make sense of this?

---

### Post by toecutter on 2007-06-18
OK it just happened again. Seems about every hour of usage, while I'm using Firefox.

The machine ran all night running bittorrent and nothing happened.

After logging back in, I opened up System Log and found this in syslog:
Jun 18 22:53:02 frank-linux -- MARK --
Jun 18 23:13:02 frank-linux -- MARK --
Jun 18 23:16:30 frank-linux gconfd (frank-13320): Received signal 15, shutting down cleanly
Jun 18 23:16:30 frank-linux gconfd (frank-13320): Exiting
Jun 18 23:16:30 frank-linux gdm[13254]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 18 23:16:41 frank-linux gconfd (frank-15570): starting (version 2.18.0.1), pid 15570 user 'frank'
Jun 18 23:16:41 frank-linux gconfd (frank-15570): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 18 23:16:41 frank-linux gconfd (frank-15570): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 1
Jun 18 23:16:41 frank-linux gconfd (frank-15570): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 18 23:16:41 frank-linux gconfd (frank-15570): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 18 23:16:41 frank-linux gconfd (frank-15570): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 18 23:16:42 frank-linux NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jun 18 23:16:42 frank-linux gconfd (frank-15570): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 0
Jun 18 23:16:42 frank-linux NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 18 23:17:01 frank-linux /USR/SBIN/CRON[15698]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

and this was in kern.log:
Jun 18 00:11:08 frank-linux kernel: [ 1856.438873] Bad page state in process 'firefox-bin'
Jun 18 00:11:08 frank-linux kernel: [ 1856.438874] page:ffff81003fe899b0 flags:0x0100000000000000 mapping:0000000000000000 mapcount:0 count:1
Jun 18 00:11:08 frank-linux kernel: [ 1856.438876] Trying to fix it up, but a reboot is needed
Jun 18 00:11:08 frank-linux kernel: [ 1856.438877] Backtrace:
Jun 18 00:11:08 frank-linux kernel: [ 1856.438880] 
Jun 18 00:11:08 frank-linux kernel: [ 1856.438881] Call Trace:
Jun 18 00:11:08 frank-linux kernel: [ 1856.438885]  [__switch_to+646/688] __switch_to+0x286/0x2b0
Jun 18 00:11:08 frank-linux kernel: [ 1856.438892]  [bad_page+88/144] bad_page+0x58/0x90
Jun 18 00:11:08 frank-linux kernel: [ 1856.438904]  [get_page_from_freelist+832/1392] get_page_from_freelist+0x340/0x570
Jun 18 00:11:08 frank-linux kernel: [ 1856.438916]  [__alloc_pages+99/784] __alloc_pages+0x63/0x310
Jun 18 00:11:08 frank-linux kernel: [ 1856.438926]  [copy_strings+190/544] copy_strings+0xbe/0x220
Jun 18 00:11:08 frank-linux kernel: [ 1856.438935]  [copy_strings_kernel+33/64] copy_strings_kernel+0x21/0x40
Jun 18 00:11:08 frank-linux kernel: [ 1856.438939]  [do_execve+335/624] do_execve+0x14f/0x270
Jun 18 00:11:08 frank-linux kernel: [ 1856.438946]  [sys_execve+68/176] sys_execve+0x44/0xb0
Jun 18 00:11:08 frank-linux kernel: [ 1856.438951]  [stub_execve+103/176] stub_execve+0x67/0xb0
Jun 18 00:11:08 frank-linux kernel: [ 1856.438963] 
Jun 18 00:48:24 frank-linux kernel: [ 2803.775051] usb 2-1: USB disconnect, address 4
Jun 18 00:48:24 frank-linux kernel: [ 2803.821623] usb 2-1: new full speed USB device using uhci_hcd and address 5
Jun 18 00:48:25 frank-linux kernel: [ 2803.892239] usb 2-1: configuration #1 chosen from 1 choice
Jun 18 00:48:25 frank-linux kernel: [ 2803.894720] hub 2-1:1.0: USB hub found
Jun 18 00:48:25 frank-linux kernel: [ 2803.895518] hub 2-1:1.0: 2 ports detected
Jun 18 01:53:55 frank-linux kernel: [ 4439.655348] usb 2-1: USB disconnect, address 5
Jun 18 01:53:55 frank-linux kernel: [ 4439.703599] usb 2-1: new full speed USB device using uhci_hcd and address 6
Jun 18 01:53:55 frank-linux kernel: [ 4439.774122] usb 2-1: configuration #1 chosen from 1 choice
Jun 18 01:53:55 frank-linux kernel: [ 4439.776601] hub 2-1:1.0: USB hub found
Jun 18 01:53:55 frank-linux kernel: [ 4439.777399] hub 2-1:1.0: 2 ports detected
Jun 18 07:06:01 frank-linux kernel: [12262.181376] gnome-video-thu[20171]: segfault at 0000000000000010 rip 00002b3162d9eb40 rsp 00007fff4d289ae8 error 4
Jun 18 07:16:26 frank-linux kernel: [12602.472700] warning: many lost ticks.
Jun 18 07:16:26 frank-linux kernel: [12602.472702] Your time source seems to be instable or some driver is hogging interupts
Jun 18 07:16:26 frank-linux kernel: [12602.472708] rip __do_softirq+0x54/0xd0

the hourly cron thing was bold as I was looking at it, then went un-bold. what is that cron process? why is it hourly?

---

### Post by H.E. Pennypacker on 2007-06-18
What happens if you are using another browser like Epiphany or Opera?  Download and install either or both of these browsers, and see if Ubuntu is still crashing.  If it does not crash with a non-Firefox browser, we can safely assume Firefox is the issue.

You may need to re-install Firefox if turns out Firefox is the issue.

---

### Post by toecutter on 2007-06-18
OK :) Now trying Epiphany but I hope this isn't a workaround solution, I do like my Firefox add-ons and such. 

any idea what the deal is with that hourly cron thing? sorry for the technical terms :)

---

### Post by Crafty Kisses on 2007-06-18
> **toecutter said:**
> Thanks for that, I've got console open now and nothing strange is popping up or showing '99%' except what I assume is the 'idle' note ('99% id').

I've got a pretty strong system apart from just 1gb of ram so I wouldn't expect the system itself to complain, my initial thought is that this is Firefox doing this. 

I'm wondering if I should see if this happens with 32-bit Firefox but I had full system crashes (shutdowns) with Swiftfox and Firefox 32-bit when I was running Edgy and I'd hoped that running Feisty on a fresh install (new HD even) would have 'cured' the problem. 

Is there any way to note what happened BEFORE a crash, as I suspect this command won't tell me that?

You might want to try "Swiftfox" and see after you install that if it still crashes.

---

### Post by toecutter on 2007-06-18
Thanks, I remember now that Swiftfox uses the Firefox add-ons! :D

---

### Post by H.E. Pennypacker on 2007-06-19
> **toecutter said:**
> OK :) Now trying Epiphany but I hope this isn't a workaround solution, I do like my Firefox add-ons and such. 

any idea what the deal is with that hourly cron thing? sorry for the technical terms :)

It's not a work around.  We're just trying to see what is causing the problem.  No solution is being offered at this time.

---

### Post by Rui Pais on 2007-06-19
> **Codename said:**
> You might want to try "Swiftfox" and see after you install that if it still crashes.

yes, but swiftfox uses the same firefox profile, so if th OP is having a bad add-on or a broke profile problem may persist... 

May i suggest close any running firefox and do:
```
mv .mozilla/firefox .mozilla/firefox_BAKUP
```
and then restart and play a little with ff to see if it happens again.


Another suggestion, instead of swiftfox, try [swiftweasel.]("http://swiftweasel.sourceforge.net/") 
Same thing with more freedom and it won't use your firefox profile. [Here a thread]("http://ubuntuforums.org/showthread.php?t=442812") with an how-to.

---

### Post by toecutter on 2007-06-19
Thanks Pennypacker - I was hoping it wasn't a workaround :) I see that someone else is having possibly the same problems when using browsers so I hope it's not widespread and is sorted out with everyone's help :)

Rui Pais - I've done the backup and will run Firefox again and post results.

Do the syslog copy and pastes help with diagnosis?

---

### Post by Crafty Kisses on 2007-06-19
> **Rui Pais said:**
> yes, but swiftfox uses the same firefox profile, so if th OP is having a bad add-on or a broke profile problem may persist... 

May i suggest close any running firefox and do:
```
mv .mozilla/firefox .mozilla/firefox_BAKUP
```
and then restart and play a little with ff to see if it happens again.


Another suggestion, instead of swiftfox, try [swiftweasel.]("http://swiftweasel.sourceforge.net/") 
Same thing with more freedom and it won't use your firefox profile. [Here a thread]("http://ubuntuforums.org/showthread.php?t=442812") with an how-to.

That should work too. :D

---

### Post by toecutter on 2007-06-19
Well it's definitely Firefox...it's crashed on me twice since I last posted. Swiftfox won't start properly for me so I'll remove that and try Swiftweasel. Epiphany seems to work fine (hell, it doesn't crash!) but I have dozens and dozens of bookmarks I'd have to import in (I'm sure there's a utility to do that, I'm just pretty annoyed right now!)

---

### Post by toecutter on 2007-06-19
Well...it seems to be anything remotely connected to Firefox! Swiftweasel crashed as well. The more tabs open, the quicker it goes, which makes sense. 

I'm on Epiphany now. Have to figure out how to import Firefox bookmarks. Might try Opera too.

---

### Post by toecutter on 2007-06-19
I can't get Swiftfox to run properly (will try reloading it!) but anything based on Firefox crashes pretty quickly. I was just now closing down Epiphany windows and as I was closing the last window I was kicked to the login screen again. 

I'm basically at a loss for words by now! I've put up with a lot of things to move to Ubuntu but this is definitely the most frustrating thing yet. 

I'll try installing Swiftfox again (I installed it but it just won't come up when I start it) and also try Opera but I really don't know what else to do. Will try watching some videos to see if that makes it crash out as well, as I mentioned before I'm generally in a browser whenever I'm in front of the computer.

---

### Post by Rui Pais on 2007-06-20
hi again.
Well, i doubt that reinstalling the same apps will do any difference (a WindowsTM solution? ;))

If it's a broken config or broken add-on, it's irrelevant which one you use, 'cause they all use the same profile (swiftwasel use a different one, but it makes an initial copy of your actual firefox profile and may duplicate any error there). 
I doubt it's that cause, anyway, since apparently in epiphany that happens to... but to be sure:

Close any fire/sift/fox/weasel, any browser, 
mv .mozila/firefox .mozilla/firefox_BACKUP.

Launch firefox and open a lot of tabs to see if that happens again. 

Swiftfox/weasel are heavy optimized firefoxs, that can only make the problem worst (if you were using gentoo, the 1st. advise anyone give to any app with problems is lowering optimizing flag, not raise, lol)

If the issue stills there ***after*** you rm curret profile and you restart with a fresn empty profile, that means that have another problems. 
Usually is a X related one. 
Glx, agp, mixed nvidia installations (original drivers mixed with restricted drivers).
Do you checked your .xsession-errors for errors after a "crashed" session?

---

### Post by toecutter on 2007-06-20
> **Rui Pais said:**
> Close any fire/sift/fox/weasel, any browser, 
mv .mozila/firefox .mozilla/firefox_BACKUP.

Launch firefox and open a lot of tabs to see if that happens again. 

Hi, thanks for the reply! :) I have done the backup thing already and opened a lot of tabs (the usual way I browse) and the crash happened again.

> If the issue stills there ***after*** you rm curret profile and you restart with a fresn empty profile, that means that have another problems. 
Usually is a X related one. 
Glx, agp, mixed nvidia installations (original drivers mixed with restricted drivers).
Do you checked your .xsession-errors for errors after a "crashed" session?

I run an ATI card but haven't done the Envy driver install yet (waiting to resolve other issues first! :))

Where/How can I check the .xsession-errors?

---

### Post by toecutter on 2007-06-20
Well. The frustration continues. I'm ONLY using Epiphany (i.e., no Firefox running at all after a hard boot). Had 5 tabs open, closed one, then closed another, then CRASH. No other programs running at all.

PleasePLEASE somone tell me how to check .xsession-errors so I can resolve this?

---

### Post by Rui Pais on 2007-06-20
> **toecutter said:**
> Hi, thanks for the reply! :) I have done the backup thing already and opened a lot of tabs (the usual way I browse) and the crash happened again.
ok, bad luck. 
As said i after you mention that epiphany too was crashing i don't have much hope on that. It was just to make sure.
QUOTE]
I run an ATI card but haven't done the Envy driver install yet (waiting to resolve other issues first! :))

Where/How can I check the .xsession-errors?[/QUOTE]

a simple:
```
cat .xsession-errors
```
:)

so if i understand correctly you are using the out-of-the-box drivers for ATI? (don't remember the name)

---

### Post by toecutter on 2007-06-20
Thanks for the quick reply!

for graphics, I'm using the stock out of the box drivers for ATI - maybe I should try running Envy to see if that helps? Seriously, I only started getting this crashing in the past week or so, so I'm not sure if it was an update or what that was t he final straw to the system, or what. 

I found out how to see .xsession-errors, I'll post what looks relevant...

From what I can tell, the errors file shows that the browser was looking for lots of ad popup and Flash (SWF) files/URLs, like this:
```
LoadPlugin: failed to initialize shared library /etc/RealPlayer/mozilla/nphelix.so [/etc/RealPlayer/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]
xEmbed supported in this Mozilla version
Gtk2+ supported in this Mozilla version
NewStream: The full URL is http://m.uk.2mdn.net/956107/night_day_728x90.swf?clickTAG=http%3A//ad.uk.doubleclick.net/click%253Bh%3Dv8/3577/7/3d/%252a/m%253B106821439%253B1-0%253B0%253B17122334%253B3454-728/90%253B21256916/21274809/1%253B%253B%257Esscs%253D%253fhttp%253A//adserver.adtech.de/adlink%257C82%257C121996%257C0%257C225%257CAdId%253D1390780%253BBnId%253D2%253Bitime%253D380460264%253Bku%253D133969%253Bkey%253Dvm3646a%252Bslashdot%255Fgeneral%253Bkwlp1%253Dvm3646a%253Bkwlp3%253Dslashdot%255Fgeneral%253Blink%253Dhttp%3A//www.t-mobile.co.uk/setfree
Forked sucessfully, child process PID is 7226
Starting process: /usr/bin/gnash -v -x 39854472 -j 728 -k 90 -u http://m.uk.2mdn.net/956107/night_day_728x90.swf?clickTAG=http%3A//ad.uk.doubleclick.net/click%253Bh%3Dv8/3577/7/3d/%252a/m%253B106821439%253B1-0%253B0%253B17122334%253B3454-728/90%253B21256916/21274809/1%253B%253B%257Esscs%253D%253fhttp%253A//adserver.adtech.de/adlink%257C82%257C121996%257C0%257C225%257CAdId%253D1390780%253BBnId%253D2%253Bitime%253D380460264%253Bku%253D133969%253Bkey%253Dvm3646a%252Bslashdot%255Fgeneral%253Bkwlp1%253Dvm3646a%253Bkwlp3%253Dslashdot%255Fgeneral%253Blink%253Dhttp%3A//www.t-mobile.co.uk/setfree -U http://ask.slashdot.org/comments.pl?sid=239021&cid=19577993 -P allowscriptaccess=always -P bgcolor=# -P height=90 -P quality=high -P src=http://m.uk.2mdn.net/956107/night_day_728x90.swf?clickTAG=http%3A//ad.uk.doubleclick.net/click%253Bh%3Dv8/3577/7/3d/%252a/m%253B106821439%253B1-0%253B0%253B17122334%253B3454-728/90%253B21256916/21274809/1%253B%253B%257Esscs%253D%253fhttp%253A//adserver.adtech.de/adlink%257C82%257C121996%257C0%257C225%257CAdId%253D1390780%253BBnId%253D2%253Bitime%253D380460264%253Bku%253D133969%253Bkey%253Dvm3646a%252Bslashdot%255Fgeneral%253Bkwlp1%253Dvm3646a%253Bkwlp3%253Dslashdot%255Fgeneral%253Blink%253Dhttp%3A//www.t-mobile.co.uk/setfree -P swliveconnect=0 -P type=application/x-shockwave-flash -P width=728 -P wmode=opaque - 
00:01:09: Verbose output turned on

00:01:09: Setting width to: 728

00:01:09: Setting height to: 90

00:01:09: Setting root URL to: http://m.uk.2mdn.net/956107/night_day_728x90.swf?clickTAG=http%3A//ad.uk.doubleclick.net/click%253Bh%3Dv8/3577/7/3d/%252a/m%253B106821439%253B1-0%253B0%253B17122334%253B3454-728/90%253B21256916/21274809/1%253B%253B%257Esscs%253D%253fhttp%253A//adserver.adtech.de/adlink%257C82%257C121996%257C0%257C225%257CAdId%253D1390780%253BBnId%253D2%253Bitime%253D380460264%253Bku%253D133969%253Bkey%253Dvm3646a%252Bslashdot%255Fgeneral%253Bkwlp1%253Dvm3646a%253Bkwlp3%253Dslashdot%255Fgeneral%253Blink%253Dhttp%3A//www.t-mobile.co.uk/setfree

00:01:09: Setting base URL to: http://ask.slashdot.org/comments.pl?sid=239021&cid=19577993

00:01:09: no rendering flags specified, using rcfile

00:01:09: OpenGL extension version - 1.2

00:01:09: Got double-buffered visual.

00:01:09: Created XEmbedded window

00:01:09: Couldn't find pixmap file: gnash_128_96.ico

** (gnash:7226): WARNING **: Couldn't find pixmap file: gnash_128_96.ico
00:01:09: WARNING: Resize request received while there's still no movie loaded, can't correctly set movie scale

00:01:09: WARNING: Resize request received while there's still no movie loaded, can't correctly set movie scale

00:01:09: Base url set to: http://ask.slashdot.org/comments.pl?sid=239021&cid=19577993

00:01:09: WARNING: SWF8 is not fully supported, trying anyway but don't expect it to work

00:01:09: ERROR:   FIXME: tagtype = 69

00:01:09: ERROR:   FIXME: tagtype = 75

00:01:09: ERROR:   FIXME: tagtype = 73

00:01:09: ERROR:   FIXME: tagtype = 74

00:01:09: ERROR:   FIXME: tagtype = 74

00:01:09: ERROR:   FIXME: tagtype = 74
```

This was the final bit of log, the time for this error started at 00:01:09, so this one went on a while:
```
00:01:41: ERROR: error: text style with undefined font; font_id = 8

00:01:41: ERROR: error: text style with undefined
...Too much output, ignoring rest...
```


From the same page in the Ubuntu Troubleshooting site where I found the ctrl + H command to see hidden files, I found this link for 'Flash makes Firefox crash', does this sound like a similar culprit or am I barking up the wrong tree? [http://ubuntuforums.org/showthread.php?p=1692197#post1692197](http://ubuntuforums.org/showthread.php?p=1692197#post1692197)

---

### Post by Rui Pais on 2007-06-20
i wasn't fast, you ask for the second time while i was still answering the first :lol:

About you logs. It contains a reference to OpenGL (something that i don't know if manageable by open sources ati drivers...)  and then it seems to get stuck trying to show a movie from net, without handling it quit well...

About your restricted driver option. I don't know if that would sane the thing, but i believe you should try as soon as possible. I think you need more framerates, and since you already had plan to install it. 
I would start by [official restricted modules]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") but i read a lot of good things from Envy. 
Anyway note that ATI cards can be hard and bad behaver under Linux...

Only now i note (blind guy here) you are on 64b. How do you installed you flash plugins?
Are your browsers 32 or 64b?

---

### Post by toecutter on 2007-06-20
I've been running 64-bit browsers whenever possible, I've assumed that the Firefox that was installed when I installed 64-bit Fiesty is a 64-bit Firefox, and the Swiftfox and Swiftweasel I loaded were both 64-bit versions. I haven't yet installed Flash support for these as it's a headache TBH but it's appearing that this is partially the cause of my problems. 

I did use Envy when I was running Edgy and it worked great. I'm installing it now and will update the thread when it's done and I've given the machine another test run :)

---

### Post by Rui Pais on 2007-06-20
> **toecutter said:**
> I've been running 64-bit browsers whenever possible, I've assumed that the Firefox that was installed when I installed 64-bit Fiesty is a 64-bit Firefox, and the Swiftfox and Swiftweasel I loaded were both 64-bit versions. I haven't yet installed Flash support for these as it's a headache TBH but it's appearing that this is partially the cause of my problems. 

I did use Envy when I was running Edgy and it worked great. I'm installing it now and will update the thread when it's done and I've given the machine another test run :)

they are not mutual exclusives (Is that correct term in English?) You can have both :).
For flash on 64b browser withut pain, see [here]("http://ubuntuforums.org/showthread.php?t=425672").
For an easy 32b browser with all (flash, java) see [here]("http://ubuntuforums.org/showthread.php?p=1174435").

it's late here. I'll check how it worked in the morning.
The best of lucks.

---

### Post by toecutter on 2007-06-20
Have installed Envy and Kilz's script and I've got loads of tabs open and even running YouTube and all is working perfectly so far! 

Very late here as well (England) so I'll log off. Thanks for the patience and help! :D

---

### Post by Rui Pais on 2007-06-21
Good! 
I'm glad it's working :D


Have fun 
:)

---

### Post by H.E. Pennypacker on 2007-06-21
> **toecutter said:**
> Have installed Envy and Kilz's script and I've got loads of tabs open and even running YouTube and all is working perfectly so far! 

Very late here as well (England) so I'll log off. Thanks for the patience and help! :D

I was going to suggest that you delete uninstall Firefox, delete .mozilla (the hidden folder in your home folder), and re-install it, but it looks like Epiphany has crashed too.  How about Opera?

I realize we're experimenting with your computer, but it is important to know the root cause of this.  If Epiphany did crash on its own, please try Opera.  Epiphany is related to Firefox.

I understand you have found Envy, but if things go wrong, again, install Opera.

---

### Post by Ptero-4 on 2007-07-02
Also from those logs you posted it seems that your crashes can be related to gnash. I know b/c I tried it once in the old mac in my house and it made firefox crash a lot, I fixed firefox by removing gnash.

---

### Post by cemptor on 2007-07-15
I have been having the exact same problem for the last couple of weeks. I've been using Fiesty x86_64 for the last 3 months without a hitch, never had any issues. It basically behaves as if someone issues a log off command in Gnome.

The only thing remarkable in the last couple of weeks was that I tried to get flash working in the 64. I have installed gnash and various things based on one of the scripts written in the forums. However have not got it to work.

Will try removing gnash and see if this goes away.

---

### Post by maruhana on 2007-11-14
Hello Everyone my Mozila browser crashes too. When i open more than window or more than 2 tabs.Cpu2 usage jumps instantly to 99%.I'm kinda new to Ubuntu don't know much about Linux yet.I downgrade effects on my computer I though that was a problem but no changes it still crashes

I run Ubuntu 7.10 32 bit
Pentium 4 @3.73ghz
4gb memory
250 gb hard drive
Nvidia video card

Screenshot

---

