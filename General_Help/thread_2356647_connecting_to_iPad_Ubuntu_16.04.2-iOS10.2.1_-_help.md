---
title: "connecting to iPad Ubuntu 16.04.2-iOS10.2.1 - help please"
date: 2017-03-25
forum: General Help
---

### Post by Andrew F in Australia on 2017-03-25
Hi All,

I've had students record work (videos) on 15 iPads and am trying to transfer the videos onto a laptop for editing.

In the past, I've had no problems connecting iPads to the computer (approx 12 months ago was the last time I did this)

Today, the iPad detects photos, but has errors in connection. It appears to mount OK

Error messages include:
shotwell could not claim the USB device
Failed to connect to lockdownd service on the device.

These include:

installing iOSTransferGUI-master (could not run in Python - unmet dependencies)
```
root@horace-P57:/mnt/Data/ipad_access_python_script/iosTransferGUI-master# chmod a+x TransferGUI.py 
root@horace-P57:/mnt/Data/ipad_access_python_script/iosTransferGUI-master# !90
./TransferGUI.py 
Traceback (most recent call last):
  File "./TransferGUI.py", line 8, in <module>
    from gi.repository import Gtk, GdkPixbuf, Gdk
ImportError: No module named gi.repository
root@horace-P57:/mnt/Data/ipad_access_python_script/iosTransferGUI-master#
```

installing 
[LIST]
[*]sudo apt-get install libimobiledevice-dev libfuse-dev  build-essentials from [http://recursivesolver.blogspot.com.au/2016/05/how-to-send-files-to-ipad-or-ios-932.html](http://recursivesolver.blogspot.com.au/2016/05/how-to-send-files-to-ipad-or-ios-932.html)
[/LIST]
```
root@horace-P57:/home/horace# !93
ideviceinfo
GnuTLS error: Error in the pull function.
ERROR: Could not connect to lockdownd, error code -5
root@horace-P57:/home/horace# !114
ifuse /media/Work_iPad/
GnuTLS error: Error in the pull function.
Failed to connect to lockdownd service on the device.
Try again. If it still fails try rebooting your device.
root@horace-P57:/home/horace# ifuse /media/Work_iPad/
GnuTLS error: Error in the pull function.
Failed to connect to lockdownd service on the device.
Try again. If it still fails try rebooting your device.
root@horace-P57:/home/horace# ideviceinfo
GnuTLS error: Error in the pull function.
ERROR: Could not connect to lockdownd, error code -5


```

ifuse 

```
horace@horace-P57:~$ ifuse /media/horace/
GnuTLS error: Error in the pull function.
Failed to connect to lockdownd service on the device.
Try again. If it still fails try rebooting your device.
```

Having spent about 4+ hours trying to figure this out, I now seek help if you don't mind.

Can anybody provide guidance on how to connect an iPad to Ubuntu 16.04.2 please?

(Yes, I also googled lockdownd service iPad enable without success as well.)

With many thanks in advance for any suggestions you are able to provide.

Andrew F

---

### Post by aokurami on 2017-03-25
**Hello, Andrew!**

Let me clarify some things, maybe I could help you. (When I've seen your post, I decided to try connecting iPad myself. You'll be surprised, I've got the same problem).

1. Do you get a prompt on your iPad screen: "Trust this Computer?".
2. Does something happen when you click "Trust"?
3. Does iPad pop up in your mounted devices list?

---

### Post by Tadaen_Sylvermane on 2017-03-25
Get a mac or Windows in a vm for itunes. The filesystem on Apple devices is not a standard folder structure like you would expect. Is why nothing works. Apple does this intentionally.

---

### Post by Andrew F in Australia on 2017-03-25
Hi Aokurami

The work ones are not password protected (I need to download content off 15 of them, Tadaen, hence why I'm avoiding iTunes if possible.)

On our own iPad, if I click trust, no change - it does appear in my mounted devices list, but doesn't show files, just recognises there's photos on there and has a radio button for Shotwell. Click that and nothing happens

---

### Post by eura on 2017-04-12
Hello Andrew this have been a issue since September, I don't know why we need to struggle with it,why can't Ubuntu fix this but here is the way to fix it 
[https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1623666](https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1623666)
Martins ppa [https://launchpad.net/~martin-salbaba/+archive/ubuntu/ppa+libimobiledevice/+packages]("https://launchpad.net/%7Emartin-salbaba/+archive/ubuntu/ppa+libimobiledevice/+packages")
 and #29 work for me, good luck / Per

---

