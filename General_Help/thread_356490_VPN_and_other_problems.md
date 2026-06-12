---
title: "VPN and other problems"
date: 2007-02-08
forum: General Help
---

### Post by Mathiasdm on 2007-02-08
I have the following few problems after installing Edgy:

1. I've installed kvpnc, but when I click to run it, I get an error: "Executing child-process 'su-to-root' failed." (No such file or directory)

2. I also have network-manager installed, and tried to get networkmanager-vpnc (a plug-in) working. The plug-in can be found at [http://bootlab.org/~j/NetworkManager/](http://bootlab.org/~j/NetworkManager/) . Sadly, the plug-in seems to depend on libdbus-1.2, while Ubuntu has 1.3 in the repositories. How do I solve this problem?

3. I have a FAT32 partition with Windows installed. When I select a folder and click 'Verwijzing maken' (in English: make a link), I get an error, stating I don't have permission to do this.

How do I solve these issues? They're not very big issues, but they are annoying, and leave a bad impression.

Thank you very much, to anyone who would like to help me!

---

### Post by sbats on 2007-02-08
Hi,

I had the same problem. Gave up on kvpnc and just installed vpnc.

In Kuntu, edgy, I used the Adept Package Manager to install vpnc. Then I found the following article and followed his instructions, included below,  for vpnc configuration:

[http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/#comment-281](http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/#comment-281)

"Installing VPNC:
Enter the following command in the terminal
sudo apt-get install vpnc resolvconf
This will install vpnc in your system. Once installed, you have to create a <filename>.conf file in /etc/vpnc/ where <filename> is the name you give (without the <>). Enter the following command to create a file called myoffice.conf
sudo gedit /etc/vpnc/myoffice.conf
and copy and paste the following in that file.
IPSec gateway xxx.xxx.xx.xxx
 IPSec ID <group name>
 IPSec secret <group password>
 Xauth username <username>
Enter the IP address of your company&#8217;s server under IPSec gateway. I got the IP address when I started the Cisco VPN client (see the output above. It&#8217;ll be under server address). I got the group name by opening the .pcf file I got from my company&#8217;s website. Replace <group name> with that group name. I got the group password also from that file. The password will be encrypted with lots of characters. Copy those characters, go to this page and paste those characters in the password box and click the Decode button. It&#8217;ll give you the password. Copy that password and paste it under the IPSec secret by replacing the <group password>. Enter your username for <username>. Save the file and close.
Enter this command to start vpnc
sudo vpnc myoffice (name of the conf file you created)
It&#8217;ll ask you to enter the password and once entered, it&#8217;ll connect to your office&#8217;s server.
If you want to disconnect, issue the following command
sudo vpnc-disconnect"

When I had the VPNC working I then wrote a script that tests if the vpncd is running. If it is not, then the script starts it. If it is then the script stops it.
1. i think you need to be root
 sudo su
 password
 2. use vim to create a new file. I put it in usr/local/bin so it would be in my path:
 vim /usr/local/bin/vpn
 3. Add the following lines then save and close the file:
 if ps -e | grep vpn
 then echo &#8220;Stopping VPN&#8221;
 vpnc-disconnect
 else echo &#8220;Starting VPN&#8221;
 vpnc
 fi
 4. Make it executable for superuser:
 chmod 700 /usr/local/bin/vpn
 5. Now as superuser, whenever you run vpn if vpnc is not running it will connect your vpn. If vpnc is running it will disconnect it.
Works very nice.
I even added a button on my tool bar for itthe vpnc configuration direction

---

### Post by Mathiasdm on 2007-02-09
Thank you for that :)

---

