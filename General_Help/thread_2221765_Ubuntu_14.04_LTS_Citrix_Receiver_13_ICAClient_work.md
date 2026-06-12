---
title: "Ubuntu 14.04 LTS Citrix Receiver 13 ICAClient working"
date: 2014-05-03
forum: General Help
---

### Post by jeff57 on 2014-05-03
In this post I willexplain how I installed Citrix Receiver (version 13) on Ubuntu 14.04 LTS on and i686


Go to CitrixReceiver for Linux Download Page. 
[http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-130.html](http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-130.html)

Pick the generic tar.gz-versionunder 32-bit (it was suggested to do this for 64-bit Ubuntu too).


Then:
$ cd ~/Downloads


(this will make a missing folder for the tar file:)
$ mkdir citrixtmp
$ cd citrixtmp
$ tar -xzf../linuxx86-13.0.0.256735.tar.gz  (or whatever it is)


(install, not asroot)
$ ./setupwfc
   (choose 1=install
    answer yes toall questions
    use all defaults
    finally, 3=exitinstaller)


I went to Firefox and pointed to my NovelAspect citrix server link.
I was able to log on but at the point of starting my program (Quick books Enterprise)
I got Error message: "I have chosen NOT to trust "AddTrustsExternal CA Root" the issuer of the servers (SSL Error 61)

I went to:
[https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=9&nav=0,1](https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=9&nav=0,1)


to download AddTrustExternalCARoot.crt into the Downloads directory.. as it usually does. 


Then I opened a terminal and from the command line: sudo nautilaus  (so I can not use the little pretty pictures of the files)
which gives me the graphic display version of the file manager
I cut the downloaded  AddTrustExternalCARoot.crt from the Download directory and
pasted it into ICAClient/linuss86/keystore/cacerts  

I clicked on the Quickbooks icon without even restarting Firefox, SSL Error 61 was gone. And.
Quickbooks started in the Citrix session after a few minutes of sorting itself out during which I thought it froze.
I don't know if this is going to work with other users on this system or I have to do it again since I was was sudo and not root.

I know there is much more elegant ways to get this done. I patched it together from lots of other generous folks.
I ended up with a ICACleint directory using the tarball approach. My first attempts with the deb failed but I think it could work.
I read that I could find out what dependencies were missing and needed using the tar approach and command line tar inquiries regarding the tar installation but never needed to inquire. It took way longer to sort out the certificate thing and my impression is there are still many other ways to do it.):P

---

### Post by giancarlo-furia-gmail on 2014-05-27
[COLOR=#000000]Thanks a lot!

[/COLOR]a small change 

I cut the downloaded AddTrustExternalCARoot.crt from the Download directory and
pasted it into** /home/myname/ICAClient/linuxx86/**keystore/cacerts

---

### Post by guss606 on 2014-07-05
Hello jeff57

Thank you very much for your How-to. 

I have Xubuntu 14.04 installed, i followed your tutorial until I went to Firefox and pointed to my citrix server link, I was able to log on but at the point of starting any program nothing happens! even if i run the Citrix Reciever from the menu also nothing happens at all!

Any help is much appreciated.

Thanks,

---

### Post by eraldtroja on 2014-08-21
Hello Jeff57,

thanks for the tutorial.  I am running 14.04 LTS and I I have followed your guide 100%.  The problem stemmed when my university decided to use SSL for their Citrix offfered programs.  They are using DigiCert certificates for SSL purposes.  

I connect to the site via [https://remote.gc.cuny.edu](https://remote.gc.cuny.edu)  If you inspect the SSL you will notice that it relies on 3 things:

1) DigiCertHighAssuranceEVRootCA (root CA)
2) DigiCertSHA2HighAssuranceServerCA (server CA)
3) *.gc.cuny.edu wild card SSL

I have used Firefox to export all 3 certificates in pem format and I have placed them inside  and I have used the c_rehash command on the following directory as well:

/home/username/ICAClient/linuxx86/keystore/cacerts

They have 444 perms and they are all reporting as .pem files.  I have tried with .pem extension or .crt extension, it does not matter.

Firefox is set to load the following upon seeing an .ica file:

/home/username/ICAClient/linuxx86/wfica.sh 

I am yet to get it work properly on this machine and I think I have followed 100% correctly your guide.

I get the following error 

"SSL error  Contact your help desk with the following iformation: The security certificate *.gc.cuny.edu could not be validated (SSL provider code: unable to get local issuer certificate, SSL error 86)"

If I remove the wildcard SSL cert from the /home/username/ICAClient/linuxx86/keystore/cacerts directory it turns into a SSL error 61

Any further advise from anyone else?

Thank you in advance

---

### Post by jiri-kovarik on 2014-09-06
Hi eraldtroja, 

I'm currently having exactly the same problem as you - connecting to a URL secured with wildcard SSL certificate. Have you found a solution to this issue already?

Cheers

---

### Post by gustavo10 on 2014-09-10
Same problem...

---

### Post by vinny6 on 2014-09-16
> **eraldtroja said:**
> Hello Jeff57,
"SSL error  Contact your help desk with the following iformation: The  security certificate *.gc.cuny.edu could not be validated (SSL provider  code: unable to get local issuer certificate, SSL error 86)"

If I remove the wildcard SSL cert from the  /home/username/ICAClient/linuxx86/keystore/cacerts directory it turns  into a SSL error 61

Any further advise from anyone else?

Thank you in advance


Solved the wildcard certificate problem. I had gotten to the point of resolving the SSL 61 error, only to bump into the SSL 86 error.

 (my school's Citrix Server is hosted at [apps.sunybroome.edu]("http://apps.sunybroome.edu") but the bottom level SSL Cert was simply [*.sunybroome.edu]("http://*.sunybroome.edu"))

This is what I did:


[LIST=1]
[*]Navigated to my school's Citrix website and downloaded the bottom-level certificate (I had already added the two top level certificates) 
[*]**Key Step:** It wanted to download as "***.sunybroome.edu**" but I *changed *it to match the URL of the Citrix Server, "**apps.sunybroome.edu**" 
[*]Attempted to navigate to **/home/username/.ICAClient/linuxx86/keystore/cacerts**, but the path ended at **/home/username/.ICAClient**,  IDK what it will look like for you 
[*]Created the necessary sub-directories in **/home/username/.ICAClient/** 
[*]Copied the newly downloaded cert 
[*]Opened a terminal and ran ```
[SIZE=3]sudo c_rehash /home/username/.ICAClient/linuxx86/keystore/cacerts[/SIZE]
``` 
[*]Restarted FireFox and...SUCCESS!!! 
[/LIST]

---

### Post by TopQuark_net on 2014-09-23
Here's how to make the Citrix Receiver v13 64-bit .deb packages work on Ubuntu Trusty 14.04:

[LIST]
[*] Download the "Receiver for Linux" and "USB Support" 64-bit .deb packages from [http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-130.html](http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-130.html)
[*] Fix the package dependencies by running:
```
mkdir icaclient.temp/
dpkg-deb -x icaclient_*.deb icaclient.temp/
dpkg-deb --control icaclient_*.deb icaclient.temp/DEBIAN/
# These perl commands simply change:
# Depends: libc6-i386 (>= 2.7-1), ia32-libs, lib32z1, lib32asound2, nspluginwrapper
# in icaclient.temp/DEBIAN/control to:
# Depends: libc6:i386 (>= 2.7-1), zlib1g:i386, libasound2:i386, nspluginwrapper, libxerces-c3.1:i386
perl -i -pe 's/Depends: (.+, )?libc6-i386(, .+)?/Depends: $1libc6:i386$2/' icaclient.temp/DEBIAN/control
perl -i -pe 's/Depends: (.+, )?ia32-libs(, (.+))?/Depends: $1$3/' icaclient.temp/DEBIAN/control
perl -i -pe 's/Depends: (.+, )?lib32z1(, .+)?/Depends: $1zlib1g:i386$2/' icaclient.temp/DEBIAN/control
perl -i -pe 's/Depends: (.+, )?lib32asound2(, .+)?/Depends: $1libasound2:i386$2/' icaclient.temp/DEBIAN/control
perl -i -pe 's/^Depends: (.+)$/Depends: $1, libxerces-c3.1:i386/' icaclient.temp/DEBIAN/control
dpkg -b icaclient.temp/ icaclient-modified.deb
rm -rf icaclient.temp/
mkdir ctxusb.temp/
dpkg-deb -x ctxusb_*.deb ctxusb.temp/
dpkg-deb --control ctxusb_*.deb ctxusb.temp/DEBIAN/
# This perl command simply changes:
# Depends: libc6 (>= 2.7-1), libcap1 | libcap2, udev, lsb-base, icaclient
# in ctxusb.temp/DEBIAN/control to:
# Depends: libc6 (>= 2.7-1), libcap1:i386 | libcap2:i386, udev, lsb-base, icaclient
perl -i -pe 's/ libcap(\d)/ libcap$1:i386/g if m/Depends: /' ctxusb.temp/DEBIAN/control
dpkg -b ctxusb.temp/ ctxusb-modified.deb
rm -rf ctxusb.temp/
```
[*] Install the packages and their dependencies by running:
```
sudo dpkg -i icaclient-modified.deb ctxusb-modified.deb
sudo apt-get -f install  # Install dependencies

```
[*] Configure Citrix Receiver by running:
```
/opt/Citrix/ICAClient/util/configmgr
```
[*] Configure Chrome/Chromium by running:
```
xdg-mime default wfica.desktop application/x-ica
```
[*] If Firefox does nothing when an application is clicked in the web interface, go to Tools -> Add-ons -> Plugins, find the "Citrix Receiver for Linux" entry, and change "Ask to Activate" to "Always Activate"
[*] If necessary (if you get a certificate error when connecting), place the root certificate associated with the server's certificate in either /opt/Citrix/ICAClient/keystore/cacerts/ or ~/.ICAClient/linuxx86/keystore/cacerts/.  (You should not need the server's certificate itself or any intermediate certificates, only the root certificate that signed them.)  You should be able to find many common root certificates in /usr/share/ca-certificates/mozilla/ (assuming you have the ca-certificates package installed), or you can export the relevant root certificate from Firefox.
[/LIST]

---

### Post by TopQuark_net on 2014-09-23
See also [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

