---
title: "Can't update/upgrade via terminal or synaptic"
date: 2013-11-07
forum: General Help
---

### Post by rapattack on 2013-11-07
Hi i went to a friends place today and i was unable to upgrade/update or install anything. Here are some of the images of some of the errors i got. I just wanted to install vlc as she is not able to play .3gp files and vlc usually does play them. Then i tried to install other players and encountered the same issue of them not wanting to install. I don't understand the errors as i am still learning but my friend knows far less. sorry i forgot to write down what version of Ubuntu she is using and will not be able to get that info from her as i cant guide her to find out. She only knows how to get on the internet and nothing else.

---

### Post by grahammechanical on 2013-11-07
Do you understand the first message that you have posted? Have you tried to do what it suggested? How did you install VLC? Through the Software Centre or by means of a PPA? You need to check the Software Sources and disable any PPAs. Try running sudo apt-get update and sudo apt-get upgrade again and note any error messages you get. You can also try

```
sudo apt-get install -f
```

as suggested. Without knowing the version it is difficult to explain how to remove PPAs because things have been moved around in the last couple of years. It does make a difference to the instructions given when Ubuntu 12.04 is compared to Ubuntu 13.10.

Regards.

---

### Post by philinux on 2013-11-07
Try to fix the broke packages first.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by jamesisin on 2013-11-07
Yes, remove any repositories you have added (you can do this through Software Sources which can be found under the Edit menu in the Ubuntu Software Center).  Once you have done that run the codes which philinux has offered.  Once you have that sorted, make sure you can run a proper update/upgrade either from the terminal (my preference) or through the GUI.

Finally, have a look at this guide for installing multimedia functionality (it needs updating since Medibuntu is gone, but ask and we should be able to assist).

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by deadflowr on 2013-11-07
> **jamesisin said:**
> Yes, remove any repositories you have added (you can do this through Software Sources which can be found under the Edit menu in the Ubuntu Software Center).  Once you have done that run the codes which philinux has offered.  Once you have that sorted, make sure you can run a proper update/upgrade either from the terminal (my preference) or through the GUI.

Finally, have a look at this guide for installing multimedia functionality (it needs updating since Medibuntu is gone, but ask and we should be able to assist).

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Software Sources can also be found in synaptic, or update manager in precise(under settings) or by using the command
```
software-properties-gtk
```
Which ever way floats your boat.

In later versions of Ubuntu, the software sources are in "Software and Updates".
+1, or 2  to running the install -f command.

---

