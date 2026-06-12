---
title: "Vista wont boot after update"
date: 2008-02-14
forum: General Help
---

### Post by mj295 on 2008-02-14
Hi 

I got up this morning to find the Vista partition doing an automatic update, which then hung on the shutdown. Now when I boot the computer up the Ubuntu works brilliantly as usual but the Vista will not boot. I get an error "windows install not found"

I have also tried to boot from the recovery partition, system restore is not available. and when I try a complete recovery (formats and reinstalls vista) it complains about C drive not being big enough???? its a 100Gb partition.

I can "cd /media/sda2" and see my windows files from ubuntu.

I realise this is not an Ubuntu problem but vista forums are useless.Please can anyone help? I'm new to Ubuntu and not ready/comfortable to use it exclusively.

Thanks

Mark

---

### Post by lswest on 2008-02-14
by "hung on the shutdown" do you mean it said "configuring updates"? it does that, as it needs to update stuff when it's not in use...just let it run through.  If that doesn't help, boot into a recovery console and use "chkdsk /f/r" i think it is (will scan the partition and fix problems that occur)

---

### Post by mj295 on 2008-02-14
Thanks, How do I get in to the recovery console, I have tried hitting F8 at all points in the boot with no luck. When I select the Vista part in the Grub menu, it goes to load windows, there is a split second blue screen flash and it reboots again.

It hung on the Vista shutdown screen, with shutdown written in the middle of the screen.

---

### Post by lswest on 2008-02-14
You have a DVD, right?  If you boot to the CD you can choose "recovery options" and then "recovery console" and then give in "chkdsk [drive, e.g. C:] /f /r"  (i'm guessing for the exact names of the options on the DVD, as the only one i have is my HP restore disk :P)

---

### Post by mj295 on 2008-02-14
Just found this in the Windows update log

2008-02-14	03:16:55:972	1172	7f88	AU	AU checked download status and it changed: Downloading is paused

2008-02-14	03:16:55:974	1172	7f88	AU	Setting AU scheduled install time to 2008-02-15 03:00:00

2008-02-14	03:17:00:970	1172	69e8	Report	REPORT EVENT: {5799BAC1-56F4-4944-862E-9DE7AFEAB1A2}	2008-02-14 03:16:55:971-0000	1	162	101	{A8944CC2-C640-42AB-96EB-CA18473B3BD7}	105	0	AutomaticUpdates	Success	Content Download	Download succeeded.

2008-02-14	03:17:00:970	1172	69e8	Report	REPORT EVENT: {3FB452A9-013A-437A-91AF-2213D98700DE}	2008-02-14 03:16:55:974-0000	1	188	102	{00000000-0000-0000-0000-000000000000}	0	0	AutomaticUpdates	Success	Content Install	Installation Ready: The following updates are downloaded and ready for installation. This computer is currently scheduled to install these updates on &#8206;15 &#8206;February &#8206;2008 at 03:00:  - Update for Windows Vista (KB937287)

2008-02-14	03:18:22:210	1172	1138	AU	AU invoking RebootSystem (OnRebootNow)

2008-02-14	03:18:22:946	1172	1138	Misc	WARNING: SUS Client is rebooting system.

2008-02-14	03:18:22:946	1172	1138	AU	AU invoking RebootSystem (OnRebootRetry)

2008-02-14	03:18:32:946	1172	1138	AU	AU invoking RebootSystem (OnRebootRetry)

2008-02-14	03:18:32:961	1172	1138	Misc	WARNING: SUS Client is rebooting system.

2008-02-14	03:18:33:101	1172	1138	AU	AU received handle event

2008-02-14	03:18:38:045	1172	1138	AU	Launched new AU client for directive 'Reboot Warning', session id = 0x1

2008-02-14	03:18:38:145	1172	1138	AU	AU received handle event

2008-02-14	03:18:42:996	1172	1138	AU	AU invoking RebootSystem (OnRebootRetry)

2008-02-14	03:18:42:996	1172	1138	Misc	WARNING: SUS Client is rebooting system.

2008-02-14	03:18:53:011	1172	1138	AU	AU invoking RebootSystem (OnRebootRetry)

2008-02-14	03:18:53:011	1172	1138	Misc	WARNING: SUS Client is rebooting system.

2008-02-14	03:18:53:073	1172	1138	AU	Launched new AU client for directive 'Reboot Warning', session id = 0x1

2008-02-14	03:18:53:183	1172	1138	AU	AU received handle event

2008-02-14	03:19:01:217	1172	1138	AU	WARNING: Initiating reboot since no user logged on

2008-02-14	03:19:01:217	1172	1138	AU	AU invoking RebootSystem (OnRebootNow)

2008-02-14	03:19:01:217	1172	1138	Misc	WARNING: Failed to reboot system, hr=8007045B.

2008-02-14	03:19:01:217	1172	1138	AU	WARNING: RebootSystem (InitiateSystemShutdown) failed, error = 0x8007045B

2008-02-14	03:19:02:948	1172	1138	Shutdwn	user declined update at shutdown

2008-02-14	03:19:02:948	1172	1138	AU	AU initiates service shutdown

2008-02-14	03:19:02:964	1172	1138	AU	###########  AU: Uninitializing Automatic Updates  ###########

2008-02-14	03:19:03:884	1172	1138	Service	*********

2008-02-14	03:19:03:884	1172	1138	Service	**  END  **  Service: Service exit [Exit code = 0x240001]

2008-02-14	03:19:03:884	1172	1138	Service	*************

---

### Post by lswest on 2008-02-14
haha, i'm not really that much of a vista techie to be able to tell you what that all means, but i'm assuming during an update it crashed and an important system file was corrupted, which would be fixed from a chkdsk /f /r

---

### Post by mj295 on 2008-02-14
> **lswest said:**
> You have a DVD, right?  If you boot to the CD you can choose "recovery options" and then "recovery console" and then give in "chkdsk [drive, e.g. C:] /f /r"  (i'm guessing for the exact names of the options on the DVD, as the only one i have is my HP restore disk :P)

No I don't have a CD.....

I have a laptop with a recovery partition. When I boot from this I get:
System Restore - no restore points are available
Hardware Check 
Re-install Vista - wipes all user data - this gives the error about the C drive being missing or too small, probably because I nicked 40Gb for the ubuntu install.

---

### Post by lswest on 2008-02-14
hmm...what's under hardware check?

---

### Post by mj295 on 2008-02-14
It runs through a few basic checks on processors memory etc, nothing too clever or helpful

---

### Post by lswest on 2008-02-14
what vista is this? business or ultimate or so?

---

### Post by mj295 on 2008-02-14
Home Premium.....

---

### Post by lswest on 2008-02-14
well, worst comes to worst you could take it to a computer repair shop and get them to run the chkdsk /r /f on it from a Home Premium DVD, they'll charge you for it, but if you don't have a DVD yourself, probably the best way to do it.  (the costs will just be for the time spent on it, not the DVD :P)

*EDIT*  If my memory serves me, most of the new laptops with vista installed come with a way to make a system restore disk (my HP laptop did, and it has a recovery partition too), maybe (once you get it fixed) might be something to check^^

*Last edit*  and if you needed to re-install Vista, you'd have to format Ubuntu and resize the partition back to the way it originally was for the restore install to work, and then add ubuntu in again later, which might be more hassle than it's worth.

*last edit...really :P* You may be able to run an ntfs chkdsk program from Linux on your drive, i don't know if it's possible, someone else might, but i don't.  And, if it does work, there is no guarantee it would fix it.

---

### Post by mj295 on 2008-02-14
I found  checkdisk option in the hardware check menu, running this has not helped, even with the fix all error option checked.....

---

### Post by mj295 on 2008-02-14
Also found this in another log

2008-02-14 03:19:05, Info                  CSI    000005b7 Creating NT transaction (seq 21), objectname [6]"(null)"^M
2008-02-14 03:19:05, Info                  CSI    000005b8 Created NT transaction (seq 21) result 0x00000000, handle @0x581c^M
2008-02-14 03:19:05, Info                  CSI    000005b9@2008/2/14:03:19:05.226 CSI perf trace:^M
CSIPERF:TXCOMMIT;7^M
2008-02-14 03:19:05, Info                  CBS    Doqe: Installing driver Update ID: Package_2_for_KB943899~31bf3856ad364e35~x86~~6.0.2.1~943899-4_RTM_neutral_GDR^M
2008-02-14 06:46:09, Error                 CBS    Doqe: Failed processing queue with hr: 0x800705aa^M
2008-02-14 06:46:09, Error                 CBS    Shtd: Failed while processing driver operations queue. hr: 0x800705aa^M
2008-02-14 06:46:09, Info                  CBS    Shtd: Failure occurred during shutdown processing after drivers were processed.  Attempting to undo driver operations.  Driver operations will be tried again on startup of Trusted Installer^M
2008-02-14 06:46:09, Error                 CBS    Failed to open SYSTEM\Select key. hr: 0x80070013^M
2008-02-14 06:46:09, Info                  CBS    Shtd: Shutdown processing complete.^M

---

### Post by mj295 on 2008-02-14
At least I've had some ideas thrown at me from this site - Ive not had 1 reply from the Vista forum!!!!!

---

### Post by danwood76 on 2008-02-14
Have you got an XP CD?
As they have chkdisk on there aswell.

When you press the F8 menu is there an option along the lines of 'Start windows with last working configuration' or something?
Choosing that may help.

---

