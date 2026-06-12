---
title: "azureus stopped working"
date: 2007-07-05
forum: General Help
---

### Post by davegod75 on 2007-07-05
I don't know what happened but azureus has stopped working.  When I try to open a torrent file azureus loads up and then just quits.  It was working yesterday.  The only thing different is that I downloaded some gimp? updates today (07/05/2007).

Anyone else experiencing this problem?

Thanks

---

### Post by NeoLithium on 2007-07-05
I've had it happen enough that I don't use Azureus anymore. However if you didn't have any torrents in queue, and have no problems acting as though it were a first install, you may wish to try to delete your /home/YOUR_USERNAME/.azureus folder.  Helped me last time.  Depending on the versoin of Ubuntu, Azureus and Java you're running you may need to replace a .jar file, I'll have to search the forums more for that problem though.

---

### Post by davegod75 on 2007-07-06
> **NeoLithium said:**
> I've had it happen enough that I don't use Azureus anymore. However if you didn't have any torrents in queue, and have no problems acting as though it were a first install, you may wish to try to delete your /home/YOUR_USERNAME/.azureus folder.  Helped me last time.  Depending on the versoin of Ubuntu, Azureus and Java you're running you may need to replace a .jar file, I'll have to search the forums more for that problem though.

interesting....i'll try that.

What program due you use instead?

---

### Post by zanazzi on 2007-07-06
DAve could u let me know if that worked B4 i try it.

I installed Azureus yesterday and tried to download a torrent over night and now Azureus wont open!

---

### Post by NeghVar on 2007-07-08
Ok, I had this same problem and have fixed it.

I first completely removed Azureus using Synaptic, then deleted the file from my Home folder. I then reinstalled the program. Once done and you open the program it will act as a brand new install, any settings you created will be erased as with any torrets being downloaded.

---

### Post by Seraed on 2007-07-09
Without having to go to extremes such as removing the .azureus folder, is there any other solution. Do we know what the actual problem is?

---

### Post by Seraed on 2007-07-22
Any one know of an update to this issue? I've had to reinstall it twice now, still buggin.

---

### Post by rjfioravanti on 2007-07-23
I have same problem... could it be a problem with the version of java we are using?

I have tried both sun's 1.5 and 1.6, I am now removing the .azureus folder and reinstalling to give that a try

---

### Post by rjfioravanti on 2007-07-23
So I tried deleting the folder and reinstalling... that worked. Then I shut it down, opened it up again and the window opens then crashes right away

This is the error message I get because I launched it from a terminal

changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00002ab8e79f2cd5, pid=5874, tid=46973644434176
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.5.0_11-b03 mixed mode)
# Problematic frame:
# V  [libjvm.so+0x3b2cd5]
#
# An error report file with more information is saved as hs_err_pid5874.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---

