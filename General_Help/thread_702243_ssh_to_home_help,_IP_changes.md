---
title: "ssh to home help, IP changes"
date: 2008-02-20
forum: General Help
---

### Post by grogger13 on 2008-02-20
I have an ssh server set up at my house and i am currently at school(college, so i dont go home often).  When i first set it up i had my sister type the commands i sent over aim into the terminal.  The only other thing i needed her to do was give me the ip address.  For about 2 days things worked and i could ssh fine, but then it stopped connecting.  I quickly realized it was that my home IP had changed, so i had to call my sister up and have her look it up again.  Tonight it must have changed again and i can't ssh.

I don't want to have to call my sister every time i need to find out the IP, is there anything i can do that will give me the IP of my home computer.

Also i have had some trouble transfering files effectively, i have used the ssh to download some stuff in bittorrent, but i goes to my home computer so i have to then transfer to my school computer.  I have had some trouble with the scp syntax and can't remember or find what i used to type for it to transfer.

If there is a way for me to download it directly to my computer through the ssh i would really like to know.

---

### Post by p_quarles on 2008-02-20
First, you can register a domain name that will keep up-to-date with your dynamic IP address here:
[http://www.dyndns.com/](http://www.dyndns.com/)

The directions for doing this are on their site. You'll need to install the client software from the repositories:
```
sudo apt-get install ddclient
```
and then use their customized configuration file.

Once you have a reliable SSH way of linking to your home computer, you can set it up as a networked drive using whatever protocol you like. Since it's a remote connection via a public network, I would recommend using SSHFS, which uses the same encryption as SSH/SCP.

---

### Post by grogger13 on 2008-02-20
About that DynDns, i have registered for an account.  Would i have to buy and create a domain name.  Im not really sure how i would use this and i don't want to pay for a domain name, thats just not worth it.

---

### Post by freelinuxhelp on 2008-02-20
I don't know if dyndns requires a domain name, but I use no-ip.org without one. the url for my home network is myusername.no-ip.org

---

