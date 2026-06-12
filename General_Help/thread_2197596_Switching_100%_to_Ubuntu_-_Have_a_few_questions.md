---
title: "Switching 100% to Ubuntu - Have a few questions"
date: 2014-01-04
forum: General Help
---

### Post by marc13 on 2014-01-04
After seeing how Windows 7 makes my life miserable, by once again crashing and preventing me from accessing data and having to go through a nightmare to get parts of my data back, I am doing a full switch to Ubuntu as soon as my new harddrive arrives. There are however a few things I enjoy about Windows, simply because "everything" consumer wise is being developed primarilly for Windows (sadly). Right now, on my old experimentary laptop, I am sitting on a Ubuntu, and I love it. Feels like freedom!

1) My printer, a HP Photosmart, doesnt seem to have the drives I need. The printer is however getting old, so I may as well get a new one, but which printer would work flawlessly with Ubuntu? 

2) I used to encrypt the entire harddrive with Truecrypt, on the boot level. I know Truecrypt cannot do this for Ubuntu. What alternatives are there? 

3) Flash! Flash is a huge huge problem, and I cant get my current flash working. Any suggestions and ideas are more than welcome, as I desperately need this working.

4) VPN services? I need an easy to install VPN client that I can connect/discconect to on the fly? Any suggestions here? Preferably free as well. 

5) Any other software I cant live without that I havent checked? Anything important that makes my daily life even better with Ubuntu? 

And hello to all in my new community ):P

---

### Post by grier-devon on 2014-01-04
Hello There,
glad to hear you are making the full switch over, I did back with Ubuntu 10.04. With printers it is always safe to use Hp printer since there is an Hp tool in the software center. In my experience the Hp tool in our software center is better then the one built for Windows and takes less time to setup the printer. With Flash if you are using Firefox then install the ubuntu restricted extras from the software center. We also have Chrome which has Flash built in and if you prefer Chromium there is a PPA to install the "pepper" plugin from chrome to get flash support. Unsure of what to use for the other stuff but I am sure a more experience user with those tools will give you an answer on those.

---

### Post by buzzingrobot on 2014-01-04
1.  A good number of HP printers require a proprietary driver from HP.  HP maintains a site that can be helpful: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html).

A typical Ubuntu installation includes the "hplip" package that provides support for HP machines.  A package that is in the repos, but not installed by default, called "hplip-gui" is a tool that, with some help from the user -- you need to know how your printer is talking to your machine -- will download and install the correct driver from HP. (The same driver can be found at hplipopensource.com.) This will install the printer, let you set it up, and print a test page.  When I use it, I then set the printer as the default via "Printers" in "Settings." (It will also put an HP applet in the panel; you can get rid of it via its preferences.)

2. The Ubuntu installer has an option to encrypt your /home folder.  I don't encrypt, so I can't add anything beyond that.

3.  The installer has another option to include some codecs, etc., including Flash.  It's also in the repos as "flashplugin-installer" and it's included in "ubuntu-restricted-extras" which bundles some proprietary bits, Microsoft fonts, etc. 

4. Can't recommend anything re: the VPN, but I'm sure others can.

---

### Post by jjmarc on 2014-01-04
First off, Welcome to Ubuntu!\\:D/ Here's my answers to your questions:

1) There is an HP tool in the Ubuntu Software Center that should be able to set up your printer fairly easily. I don't use an HP printer, so I can't say anything beyond that.

2) When you first install Ubuntu, you have the option to encrypt your home folder, which has most of your account data in it. If you decide to do it after installation, there are plenty of tutorials on the internet on how to do it ([example]("http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu")).

3)Chrome automatically updates flash, and there is a flash plugin installer tool in the Ubuntu Software Center. In my personal experience, Chrome is a lot slower to update Flash (and it's a lot harder to do manually) than you can with Firefox, so I recommend Firefox for flash related sites.

4)Ubuntu has a VPN client installed out of the box, so you should be good there. To get to it, you click the connection icon in your taskbar (the 2 arrows right next to each other) and go to VPN connections.

5) I highly recommend Wine, which is a Windows program loader for Linux. Another great tool is GUFW, which is a GUI for configuring Ubuntu's default firewall, UFW.

---

### Post by caymus on 2014-01-04
For vpn you have all wat you need into gnu/linux, for pptp or openVPN (pptp is crap & cheap, but easy to config, i thing this is the default used into windause also).

for crypt:

I pesonally crypt files only by gpg or openssl because: because... ^^

```

crypt:
openssl des3 -salt -in picture.jpg -out picturecrypte.des3

decrypt:
openssl des3 -d -salt -in picturecrypte.des3  -out picture.jpg -k passwd

```

gpg work +- the same way.

But if you need to crypt the whole hdd, take a look at [https://wiki.archlinux.org/index.php/Disk_Encryption](https://wiki.archlinux.org/index.php/Disk_Encryption)

---

### Post by marc13 on 2014-01-04
> **buzzingrobot said:**
> 1.  A good number of HP printers require a proprietary driver from HP.  HP maintains a site that can be helpful: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html).

A typical Ubuntu installation includes the "hplip" package that provides support for HP machines.  A package that is in the repos, but not installed by default, called "hplip-gui" is a tool that, with some help from the user -- you need to know how your printer is talking to your machine -- will download and install the correct driver from HP. (The same driver can be found at hplipopensource.com.) This will install the printer, let you set it up, and print a test page.  When I use it, I then set the printer as the default via "Printers" in "Settings." (It will also put an HP applet in the panel; you can get rid of it via its preferences.)

2. The Ubuntu installer has an option to encrypt your /home folder.  I don't encrypt, so I can't add anything beyond that.

3.  The installer has another option to include some codecs, etc., including Flash.  It's also in the repos as "flashplugin-installer" and it's included in "ubuntu-restricted-extras" which bundles some proprietary bits, Microsoft fonts, etc. 

4. Can't recommend anything re: the VPN, but I'm sure others can.

For number 3, I cant seem to find anything related to the mentioned "ubuntu-restricted-extras". What is the "ubuntu-restricted-extras"? 
I just looked at the Flash extensions in the software center, and didnt seem to have any extensions that were related to the "ubuntu-restricted-extras" or such. Please elaborate if you can.

---

### Post by sudodus on 2014-01-04
Hi marc13,

2. Disk encryption: The guide for iso testers is also useful for people who are 'only' users. I have tested it with the current released versions and know that it works. See this link

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

3. Depending of flavour of Ubuntu run

```
sudo apt-get install ubuntu-restricted-extras
```
or
```
sudo apt-get install lubuntu-restricted-extras
```
...
and you should have flash available the next time you start Firefox.

---

### Post by grier-devon on 2014-01-04
When you go into the software center if you scroll down you should see it listed under top rated.

---

