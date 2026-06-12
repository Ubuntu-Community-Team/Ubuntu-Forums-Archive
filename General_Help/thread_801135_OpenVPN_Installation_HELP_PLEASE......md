---
title: "OpenVPN Installation HELP PLEASE....."
date: 2008-05-20
forum: General Help
---

### Post by okaloosaman on 2008-05-20
I am currently setting up OpenVPN on my 8.04 LTS

Here is my syntax.  I have red many threads that have not solved this issue


james@james-desktop:/etc/openvpn/easy-rsa/2.0$ ./vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/2.0/keys
james@james-desktop:/etc/openvpn/easy-rsa/2.0$ source ./vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/2.0/keys
james@james-desktop:/etc/openvpn/easy-rsa/2.0$ ls
build-ca          build-key-server  Makefile              sign-req
build-dh          build-req         openssl-0.9.6.cnf.gz  vars
build-inter       build-req-pass    openssl.cnf           whichopensslcnf
build-key         clean-all         pkitool
build-key-pass    inherit-inter     README.gz
build-key-pkcs12  list-crl          revoke-full
james@james-desktop:/etc/openvpn/easy-rsa/2.0$ sudo ./clean-all
[sudo] password for james: 
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
james@james-desktop:/etc/openvpn/easy-rsa/2.0$ sudo ./build-ca
  Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys.
james@james-desktop:/etc/openvpn/easy-rsa/2.0$ 



Please help solve this Its really making me angry

---

### Post by emkamau on 2008-06-10
Any help here?. I'm having the same problem. Is this a bug in OpenVPN?

emk

---

### Post by slack42 on 2008-06-20
I am also having the same problem. It's a constant loop that seems to do nothing. Very frustrating.

One thing I noticed looking in the var file is 

export PKCS11TOOL="pkcs11-tool"

I don't have this tool installed on my system and couldn't find it in synaptic. Don't know if not having that tool makes a difference but I have done a lot of googling and can't find a solution anywhere.

---

### Post by slack42 on 2008-06-20
Hi, I don't know if this thread is still alive but I figured out this problem. 

I was able to install pkcs11-tool, turns out that it is a part of opensc. I also installed libopensc2 just in case but one of them worked and now I got the package installed. 

Then I went back to the directory and went threw the process of setting up the certificates again but this time I did two things different. First I became root with "sudo -s" and then I created the keys directory because it looked like it wasn't being created for some reason. 

Once I did that I went threw the steps again and when I did ./build-ca the script finally worked and presented me with the questions that the HOWTO on the openVPN page said that it would. 

Hope this helps someone, it was very frustrating for me to figure out how to get this working. Getting the VPN network working will be the next challenge.

---

### Post by beaker15 on 2008-09-16
I was stuck on this for ages and got really frustrated. the solution (for me anyway) turned out to be quite easy really.

1. Restart the PC
2. Open the terminal and type *sudo su *to log in as root
3. move to the easy-rsa directory (on mine, the files are in easy-rsa/2.0/)
4. type *mkdir keys*
5. type *source ./vars*
6. type *./clean-all*
7. type *./build-ca*

all the same commands as before but having created the keys directory and actually being logged in as root, instead of running it with sudo seemed to do the trick

---

### Post by maxchock on 2009-08-09
> **beaker15 said:**
> I was stuck on this for ages and got really frustrated. the solution (for me anyway) turned out to be quite easy really.

1. Restart the PC
2. Open the terminal and type *sudo su *to log in as root
3. move to the easy-rsa directory (on mine, the files are in easy-rsa/2.0/)
4. type *mkdir keys*
5. type *source ./vars*
6. type *./clean-all*
7. type *./build-ca*

all the same commands as before but having created the keys directory and actually being logged in as root, instead of running it with sudo seemed to do the trick

hey, thanks for your info. i think this at least save me another hour to "debug"...

---

### Post by Draiden on 2009-11-04
> **beaker15 said:**
> I was stuck on this for ages and got really frustrated. the solution (for me anyway) turned out to be quite easy really.

1. Restart the PC
2. Open the terminal and type *sudo su *to log in as root
3. move to the easy-rsa directory (on mine, the files are in easy-rsa/2.0/)
4. type *mkdir keys*
5. type *source ./vars*
6. type *./clean-all*
7. type *./build-ca*

all the same commands as before but having created the keys directory and actually being logged in as root, instead of running it with sudo seemed to do the trick

This is the solution to the problem of having to 'source' the ./vars.

Thanks for a couple of hours of debugging!

I didn't have to restart the system though. It worked immediately after I had created the keys directory.

Thanks a lot!

---

### Post by fooey on 2011-02-14
> **slack42 said:**
> ...I also installed libopensc2 

thx. that worked

---

