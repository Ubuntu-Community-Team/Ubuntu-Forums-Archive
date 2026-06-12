---
title: "Kindle Fire HD"
date: 2012-11-04
forum: General Help
---

### Post by kidd linux on 2012-11-04
I just baught the new kindle fire hd..I run Ubuntu 10. I keep getting the popup on the tablet to install the File Transfer driver. it tells me to go to kindle/support however it doesnt appear to have been installed or working on my pc..How  can I install the drivers for the Kindle Fire HD onto my Pc?

---

### Post by kidd linux on 2012-11-04
I have Found this to  work for me..


  	 	 	 	 	 	   Step 1. Install the libusb-dev dependency package so you can build libmtp  
 [INDENT]sudo apt-get install libusb-dev[/INDENT] Step 2. Download the latest libmtp tar.gz from here: 
[[COLOR=#000080]_http://sourceforge.net/projects/libmtp/files/libmtp/_[/COLOR][COLOR=#000080][/COLOR]]("http://sourceforge.net/projects/libmtp/files/libmtp/")

Step 3. cd into the same directory where you downloaded the new libmtp*.tar.gz and extract the tar package:  
 [INDENT]tar xvf libmtp-1.1.1.tar.gz[/INDENT] Step 4. cd into the libmtp directory you just extracted , then compile and install using configure/make/make install:  
 [INDENT]cd libmtp-1.1.1/ 
./configure --prefix=/usr 
make 
sudo make install[/INDENT] Step 5 (maybe optional). Not sure if I needed this step or not, but if everything in the last step went well, you'll now have the 69-libmtp.rules file in the current directory, and you can copy it to /etc/udev/rules.d to ensure you can access the phone through the USB. 
 [INDENT]sudo cp 69-libmtp.rules /etc/udev/rules.d[/INDENT] Step 6. Install the handy gMTP Graphical MTP file access utility:  
 [INDENT]sudo apt-get install gmtp[/INDENT] Step 7. Try to run gMTP and see if it connects to your device. If not, then refresh things by unplugging your phone, rebooting the computer, then plugging in your phone again. Then, try to launch gMTP from the Unity/Gnome menu again, see below.
  
  	 	 	 	 	 	   [IMG]http://1.bp.blogspot.com/-p6fhfPS6sZ0/Tu67DFV8SmI/AAAAAAAAExo/1HLM2B-6sxw/s320/unity_gmtp.png[/IMG] 
 


Step 8. You should see something like below when you click connect. Also you should be able to copy files to and from the device with ease.
 [IMG]http://1.bp.blogspot.com/-OsfW5m_XHqk/Tu252mAbqKI/AAAAAAAAEv0/FESZzIc50tY/s640/gMTP.png[/IMG]

---

### Post by Bucky Ball on 2012-11-04
Welcome. If this works, well done, and please mark this thread as 'Solved' from 'thread tools' at top right to help others, as I'm sure it will. ;)

My wife was talking about buying a Kindle last night, coincidentally, so this may come in handy sooner than I think!

---

### Post by verymadpip on 2012-11-11
gMTP "just works" for me; no messing about at all.

---

