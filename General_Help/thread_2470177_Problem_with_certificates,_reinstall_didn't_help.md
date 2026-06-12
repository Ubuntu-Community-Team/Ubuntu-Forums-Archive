---
title: "Problem with certificates, reinstall didn't help"
date: 2021-12-21
forum: General Help
---

### Post by kahlenberg on 2021-12-21
[COLOR=#232629][FONT=-apple-system]I am using Ubuntu 20.04 and I have problems with ca-certificates. When I run command sudo apt update, I receive a lot of errors like:[/FONT][/COLOR]
[HTML]Certificate verification failed: The certificate is NOT trusted. 
The certificate issuer is unknown.
Could not handshake: Error in the certificate verification
[/HTML]
[COLOR=#232629][FONT=-apple-system]Or when I run curl --proto '=https' --tlsv1.2 -sSf [https://sh.rustup.rs](https://sh.rustup.rs) | sh (or with -k option),[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I receive[/FONT][/COLOR]
[HTML]curl: (77) error setting certificate verify locations:
  CAfile: /etc/ssl/certs/ca-certificates.crt
  CApath: /etc/ssl/certs
[/HTML]
[COLOR=#232629][FONT=-apple-system]I tried followings without success:[/FONT][/COLOR]
[HTML]sudo apt-get install --reinstall ca-certificates

sudo ln -s /etc/ssl/certs/ca-certificates.crt /etc/pki/tls/certs/ca-bundle.crt

export CURL_CA_BUNDLE=/etc/ssl/certs/ca-certificates.crt[/HTML]

[COLOR=#232629][FONT=-apple-system]Interestingly, I discovered that half of the /etc/ssl/certs/ca-certificates.crt file has normal line-ending, other half has different line-endings.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]First half of ca-certificates.crt:[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][[IMG]https://i.stack.imgur.com/QPgd0.png[/IMG]]("https://i.stack.imgur.com/QPgd0.png")

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Second half of ca-certificates.crt:[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][[IMG]https://i.stack.imgur.com/JPTu0.png[/IMG]]("https://i.stack.imgur.com/JPTu0.png")

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I correct the file with dos2unix but I am getting still errors.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]What is the root cause of the issue and the solution?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks.[/FONT][/COLOR]

---

### Post by TheFu on 2021-12-21
The ^M endings mean that someone used an MS-DOS editor and broke the file.
I bet there is a ca package that can be reinstalled.
```

$ apt search certificate
```
> 
On my system, that returns a bunch of packages, but I'd guess these 2 are the ones:
ca-cacert/focal,focal 2019.0411-2 all
  CAcert.org root certificates

ca-certificates/focal-updates,focal-updates,focal-security,focal-security,now 20210119~20.04.2 all [installed]
  Common CA certificates

Reinstall those and see if that helps.

```
sudo apt install --reinstall ca-cacert ca-certificates
```

BTW, TLS v1.2 is known to be hacked for more than a year.  May want to force v1.3 and later.   [https://threatpost.com/nsa-urges-sysadmins-to-replace-obsolete-tls-protocols/162814/](https://threatpost.com/nsa-urges-sysadmins-to-replace-obsolete-tls-protocols/162814/) When the NSA says to the world to stop using v1.2, we should listen.

BTW, running any directly downloaded code is terrible for security.  I downlaoded the script (looks like it is a Rust setup script of some sort) and saved it locally using the command from the top page.  It worked fine. I'm unable to reproduce part of the problem. Just the **|sh** is missing, so perhaps it is a dash failure?  Try using bash instead ... or split up the task into download and run parts.

I'm unwilling to run this script on my system without looking over the entire thing. It appears to be normal Bourne shell stuff.  If it was me, I'd just get the correct  rust installer for my system/OS/platform directly from a different website. It isn't like anyone using rust in this way wouldn't be able to do that. This is not for end users.

The fact that the script is full of forced use of TLS v1.2 is a little out of date.

---

### Post by kahlenberg on 2021-12-22
Thank you for answer.
I installed ca-cacerts and tried TLSv1.3 but it is same.

I can install Rust from different website, it is not problem, I just gave this command as an example.

I am still having problem with ```
sudo apt update
```

For example:
```

Err:8 https://download.docker.com/linux/ubuntu focal Release                                                                                                                                                      
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification


Err:11 https://dl.google.com/linux/chrome/deb stable Release                                                                                                                                  
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification


Err:13 https://packages.microsoft.com/repos/ms-teams stable Release                                       
   Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification



```

---

### Post by TheFu on 2021-12-22
Looks like the issue is with 3rd party repos, not Canonical/Ubuntu ones?
I'd use some catools (perhaps openssl) to see of the cert files can be unpacked and validated.  Google said this was the answer:
```
$ sudo openssl verify  /usr/share/ca-certificates/mozilla/UCA_Extended_Validation_Root.crt 
/usr/share/ca-certificates/mozilla/UCA_Extended_Validation_Root.crt: OK
```

That just means it can be parsed, not much more.  For more comprehensive information .. [https://github.com/drwetter/testssl.sh](https://github.com/drwetter/testssl.sh) . Used that script a few months ago for something. There is some manual setup with the tool. The instructions explained clearly enough which to find and copy, where.

If something only on your system is corrupting the CA files that's different than if everyone else has the issue.  Isolating the issue to you vs the rest of the world is the first step, since I can't imagine you went out of the way to break stuff.  Corruption comes from just a few places - some accidental, hardware, and malicious.
Some things to consider and try:
[LIST]
[*]Have any other files on the system been corrupted that you've noticed?  
[*]Can you compare the files today with some from before - perhaps 3 weeks ago?  I'd use my backups to do that. It has saved me a few times over the decades.
[*]Any file system issues that required running fsck?
[*]Does the HDD SMART data all seem clean or are there potential corruption issues there?
[*]Is the problem userid specific?  Create a new userid with privileges and run the same commands. Do they work? (I doubt this will help, but 1 minute will tell)
[*]If you boot into a "Try Ubuntu" environment, does apt update and do 3rd party repos work?
[*]Do any other systems on the same network show the issue too?
[*]Is any APT caching being used?  I had to whitelist some domains for apt-cacher-ng to work with specific repos.
[*]If you do virtual machines, are those impacted?  A 10G Ubuntu Server VM will quickly show the differences. Be certain to validate the permissions.
[/LIST]

I noticed on a 20.04 system here that snaps have their fingers all in the system Certs.
```
$ locate UCA_Global_G2_Root.pem
/etc/ssl/certs/UCA_Global_G2_Root.pem
[COLOR="#FF0000"]/snap/core/[/COLOR]11993/etc/ssl/certs/UCA_Global_G2_Root.pem
[COLOR="#FF0000"]/snap/core18/[/COLOR]2253/etc/ssl/certs/UCA_Global_G2_Root.pem
[COLOR="#FF0000"]/snap/core20/[/COLOR]1270/etc/ssl/certs/UCA_Global_G2_Root.pem
```
Yuck. Hey Canonical, SNAPS ARE NOT THE ANSWER FOR EVERYTHING!  At least the mozilla cert package seems normal. For HTTPS stuff, I think this is all that gets used.
Signed packages, as provided by the repos use gpg signatures, but that happens AFTER the files are downloaded.

OT: We don't get to pick which TLS some remote server uses. That's unfortunate.  Over a year ago, I moved all my servers over to only support TLS v1.3 and nearly all the remote hacking attempts stopped from 1 specific country in Asia. It was amazing.  Then I learned that country's firewall only allowed TLS v1.2 and earlier.  The Rust guys have different requirements than my business clients have.  They want as many people to have access to the code/setup as possible, whereas I want about 50 client companies and 5000 possible client companies to have access AND NOBODY ELSE. Very different requirements.

---

