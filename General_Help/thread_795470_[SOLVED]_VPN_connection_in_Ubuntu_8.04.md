---
title: "[SOLVED] VPN connection in Ubuntu 8.04"
date: 2008-05-15
forum: General Help
---

### Post by cosine352 on 2008-05-15
Hi All,
Do anyone know how to use VPN connection in Ubuntu 8.04. I am unable to connect to my university in Ubuntu 8.04. I followed this ([original link]("http://www.stat.ufl.edu/system/vpn.shtml"))
> 1. install the packages vpnc and network-manager-vpnc using either
   using the synaptic package manager or one of the command line tools
   (apt-get or aptitude), e.g.,

      sudo apt-get install vpnc network-manager-vpnc

   This should also restart network-manager, so be prepared to
   momentarily lose your network connection (I would quit email before
   doing this).

2. Click on the network icon in your "system tray" area (the thing
   that looks like two computer monitors or like the bars on a cell
   phone if you're on wireless).  You should now see an entry for "VPN
   Connections".  Go into that menu and click "configure VPN".

3. This should open the "VPN Connections" window.  Click "Add".

4. I recommend using "UF VPN" as the Connection Name.  For the gateway
   use vpn.ufl.edu; for the group name use vpn-auth.

5. On the optional tab click "Override user name" and add your UF
   gatorlink email address (e.g., [email]yourgatorlinkusername@ufl.edu[/email]) and
   click forward and then apply.

6. You will need the UF VPN group password, which is contained in
   encrypted form in the VPN configuration file that you can download
   from:

      [http://net-services.ufl.edu/~ns/cgi-bin/vpn/vpn-clients.cgi](http://net-services.ufl.edu/~ns/cgi-bin/vpn/vpn-clients.cgi) 

   (Once you are logged in, scroll to the bottom of the page to
   download the configuration file).  The group password is given by
   the enc_GroupPwd field in the pcf file that you download.  The
   following web page will decrypt the password for use with vpnc:

      [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

7. Now you can connect to the vpn by clicking the network icon, going
   to VPN connections and clicking "UF VPN".  It will ask you for your
   password (your gatorlink password) and the group password.

8. I went ahead and clicked the button that adds the group password to
   my keyring so that I don't have to remember it in the future.  (I
   suppose that the group password might change from time to time
   though, so one might have to retrieve and enter a new one at some
   point.)


It is not connecting to VPC (doing nothing). 

Any help will be greatly appreciated. 

Thanks

---

### Post by cosine352 on 2008-05-15
It is working now (after some update I guess.).

---

### Post by bodhi.zazen on 2008-05-15
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

