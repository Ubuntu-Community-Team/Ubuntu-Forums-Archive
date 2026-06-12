---
title: "Konica IP-421 Scanning in Linux"
date: 2007-05-16
forum: General Help
---

### Post by redPirate on 2007-05-16
Now you can use Konica IP-421 to scan files and download it to a Linux PC. This is a simple step by step guide

But first my configuration:
I am using Kubuntu Fiesty
My Konica 7022/IP-421 is connected to wirless router.
I connect to the network via D-Link wirless usb stick


The Konica IP-421 can scan box can be accessed via ftp.

Step1: Open Konsole (or any other xterm)
Step 2: Type in "ftp xxx.xxx.xxx.xxx" here xxx reperesent the IP address of the Konica machine. for example 192.168.2.10. My IP is 192.168.0.200
Step 3: when asked the name type SCAN and press enter
Step 4: In password enter the 4 digit box number from which you wish to download the scanned file
Step 5: Type "binary" to change into I(mage) mode
Step 6: type "ls" to get list of the files
Step 7: type "get <filename>" to download the file to local disk
Step 8: If you want to delete the file from the photocopier type "delete <filename>"
Step 9: type "exit" to close the ftp connection to the photocopy

Note: you can type "help" after entering user name and password to get list of acceptable commands with the photocopier

Hope this helps.

---

