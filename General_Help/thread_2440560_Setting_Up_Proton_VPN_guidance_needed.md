---
title: "Setting Up Proton VPN guidance needed"
date: 2020-04-12
forum: General Help
---

### Post by mawil10132 on 2020-04-12
Simply go to;  [https://protonvpn.com/support/linux-vpn-tool/](https://protonvpn.com/support/linux-vpn-tool/)
For Ubuntu enter into command line; sudo apt install -y openvpn dialog python3-pip python3-setuptools
Next into command line; sudo pip3 install protonvpn-cli
Next into command line; sudo protonvpn init
Find your;  openvpn account user name and password (which are not the user name and password you use to sign in with.) [https://protonvpn.com/support/vpn-login/](https://protonvpn.com/support/vpn-login/)
* Below the sudo protonvpn init command there is a box filled with what to do once you get into Proton, where you will enter the openvpn account user name and password, Then select your proton plan (free, basic, plus, visionary), then default is 1., Then it asks you to confirm all so select Y for yes. Then enter into command line; 


A. I'm going to set up to run proton vpn, the instructions recommends; Linux VPN command line tool. 

B. It also says to install these; (I see there is a command line instruction that can be copies and pasted into command line. I assume that needs to be first before anything else?)
You will need the latest updates of the following dependencies installed on your Linux repository: 
[LIST]
[*]openvpn 
[*]python3.5+ 
[*]dialog (optional, needed for interactive selection) 
[*]pip for python3 (pip3) 
[/LIST]
**On Debian / Ubuntu / Linux Mint and other derivatives, please use:**

sudo apt install -y openvpn dialog python3-pip python3-setuptools
sudo pip3 install protonvpn-cli

C. Here is the first page I'm directed to which explains they prefer not manually installing. To instead use the; Linux VPN command line tool. [https://protonvpn.com/support/linux-vpn-setup/](https://protonvpn.com/support/linux-vpn-setup/)

Here is the second page for Command Line Tool; [https://protonvpn.com/support/linux-vpn-tool/](https://protonvpn.com/support/linux-vpn-tool/)

D. PS: I've never used GitHub where command line is at, I looked at it and have no idea how to download.  [https://github.com/ProtonVPN/protonvpn-cli-ng](https://github.com/ProtonVPN/protonvpn-cli-ng)

---

