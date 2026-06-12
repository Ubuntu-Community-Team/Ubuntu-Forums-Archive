---
title: "force the use of one particular https apt mirror and verify it's connection"
date: 2022-09-10
forum: General Help
---

### Post by vbgf3 on 2022-09-10
Hi,

I have a particular Ubuntu https apt update mirror that I want to use. And I want to verify it's connection. In particular I want to forbid connections to any other mirror. 

I have modified my sources.list to use that mirror.

I have made a /etc/apt/apt.conf and here is what it looks like:

```
Acquire 
{
  https
  {
        Verify-Peer "true";
        Verify-Host::csclub.waterloo.ca "true";
        Verify-Host::google.com "true"; 
        SSLCert::csclub.waterloo.ca "csclub-uwaterloo-ca.pem";
        SSLCert::google.com "google-com.pem";
        SSLKey "private.key";
        CaPath  "/etc/ssl/certs";
        Verify-Host "true";
        // AllowRanges "<BOOL>";
        AllowRedirect "false";


        Timeout "30";
        ConnectionAttemptDelayMsec "250";


        // Cache Control. Note these do not work with Squid 2.0.2
        No-Cache "false";
        Max-Age "86400";     // 1 Day age on index files
        No-Store "false";    // Prevent the cache from storing archives
        //Dl-Limit "<INT>"; // Kb/sec maximum download rate


        //User-Agent "Debian APT-CURL/1.0";
        //User-Agent "Debian APT-HTTP/1.3";
  };

```};

The above works. However if I change the csclub-uwaterloo-ca.pem" to csclub-uwaterloo-ca.bad.pem" It still works. It is as if the conf is making no difference. I mean, the connection should fail if I supply a bad pem certificate, no ?

Another problem is that I work in cafeterias a lot. I want to prevent somebody from sending me fake updates. So, I want to Always Only Connect to my One Chosen Mirror and Drop Connections from other 'mirrors'.  I have in the past received fake upgrades while doing 'sudo apt upgrade' . Seems like an attacker can slip in any file they want into my upgrade stream and have Ubuntu install it. So I hope apt.conf can let me specify a particular mirror and stick to it and drop any other connections.

---

### Post by Tadaen_Sylvermane on 2022-09-10
I'm not understanding your desire for https. The packages are in gpg signed which is checked from the keyring. They would have to modify your keyring package as well as the ones on the server to get "fake" packages into your system.

> [COLOR=#000000] I have in the past received fake upgrades while doing 'sudo apt upgrade'[/COLOR][COLOR=#000000]

This just isn't realistic unless you are using shoddy ppa's and such. Even then that is the ppa update problem, not the main ubuntu repos.[/COLOR]

---

### Post by vbgf3 on 2022-09-10
Well, after posting the above address in my apt.conf, the attackers have resorted to blocking the pub key, I get this error: 

>  GPG error: [https://mirror.fcix.net/ubuntu](https://mirror.fcix.net/ubuntu) jammy-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
E: The repository 'https://mirror.fcix.net/ubuntu jammy-backports InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.




I guess somehow now they have blocked the pub key. I won't be updating for a while. The attackers have control of the router.

---

### Post by vbgf3 on 2022-09-10
Just in case you are wondering, I copied the PPA from Ubuntu mirrors web site. Here's what unversity of waterloo is saying now: 

>   The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
Err:3 [https://mirror.csclub.uwaterloo.ca/ubuntu](https://mirror.csclub.uwaterloo.ca/ubuntu) jammy-updates InRelease


---

### Post by QIII on 2022-09-10
Who owns [https://mirror.fcix.net/ubuntu](https://mirror.fcix.net/ubuntu)?

---

### Post by vbgf3 on 2022-09-10
Clicking on ../ from [COLOR=#000000] [/COLOR][https://mirror.fcix.net/ubuntu](https://mirror.fcix.net/ubuntu)[COLOR=#000000]? reveals this page:  [/COLOR]https://mirror.fcix.net/ and it says it is spoonsered by: [COLOR=#111111][FONT=-apple-system] [/FONT][/COLOR][Fremont Cabal Internet Exchange]("https://fcix.net/")[COLOR=#111111][FONT=-apple-system] [/FONT][/COLOR]

---

### Post by oldfred on 2022-09-11
It is on the list of mirrors.
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by vbgf3 on 2022-09-19
The attacker did it again. He slipped an package to me while I was upgrading. I am sure he didn't modify the ppa, he only sent me a file, maybe spoofing the source ip, and Ubuntu swallowed it whole. I reinstalled Ubuntu in the morning, and performed an apt upgrade. And after not touching the pc for the whole day, when I returned from work and browsed Youtube, he was able to control my mouse.

So my only hope is to force confine the upgrade to originate from the ppa.

https doesn't matter much, as it only guarantees the integrity of a file in transit. But I need to guarantee that the file does come from the ppa. And if apt.conf can let me specify the certificate, then hopefully it can reject any file not originating from the ppa.

EDIT: I also now remember that the apt update list is unprotected in any way. So maybe, the attacker sent me a modified update list that includes his remote control program.

---

