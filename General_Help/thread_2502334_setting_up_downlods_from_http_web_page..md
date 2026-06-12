---
title: "setting up downlods from http web page."
date: 2024-11-10
forum: General Help
---

### Post by ulao3 on 2024-11-10
I have a site in witch I want to allow downloads. All browsers are flagging any http links as a security risk. So I tried FTP, but apparently all browsers are removing FTP as a security  risk. I use my own web server that is not secure and I have no experience setting up a secure server. Am I correct in thinking this is a lengthy process? At this time I'm not looking to pay for hosting files. I'd like to just allow downloads from the site I run. Is there no easy way to make a the http an https to allow the downloads from a browser.

---

### Post by TheFu on 2024-11-10
For anonymous downloads (i.e. non-authenticated), just use any popular web server and add SSL certs using "Let's Encrypt" certs. These are free for 90 days at a time.  Most personal websites use them.  I've been using them for a long time and update the certs every 77 days through a script. Actually, for trivial needs, the update can be 100% automatic. This is expected.  [https://letsencrypt.org/getting-started/](https://letsencrypt.org/getting-started/)   

For authenticated access, use sftp.  
[LIST=1]
[*]Install **ssh-server** and you get sftp for free.  ssh is how Unix-like OSes communicate for non-anonymous needs.
[*]Install **fail2ban** to prevent brute force attacks.
[*]Setup ssh-keys from the clients to the server. Don't use passwords.  These are the 3 commands, run on the client:
```
   $ **ssh-keygen** -t ed25519
   $ **ssh-copy-id** -i ~/.ssh/id_ed25519.pub username@remote
   $ **ssh** username@remote
```
[*]Setup port translation from the WAN router, so you don't expose 22/tcp to the internet.  Pick some random high port, say 58422/tcp and forward that to the LAN static IP of your server 22/tcp.
[/LIST]

To make access easier from the client, setup the ~/.ssh/config file with a LAN stanza and a WAN stanza for access to the server when you are on the LAN or on the WAN. They use different ports. This way, you'll never need to remember that port.  Something like this:
```
host share-lan
  user joe
  hostname 192.168.22.32
  port 22

host share-wan
  user joe
  hostname your-public-static-ip-on-the-internet-OR-DNS-name
  port 58422

```
That's it.  Now you can use that client system with any sftp-client to have access to files or to push files to the remote system.  BTW, you also have ssh access, so remote terminals can be used and about 50 other things are possible over ssh as well.  rsync, scp, backups, ssh-tunnels, SOCKS proxy, remote desktops, all leverage ssh, so the possible options are nearly unlimited.

Most Linux file managers work with sftp:// URLs after the ssh-client software is installed.  It sorta just works like browsing local disks.

If you just need a 1-time file transfer, you can also use **magic wormhole** between any two systems.  This is a bit clunky because every transfer will have a random passphrase to receive the file(s).  [https://magic-wormhole.readthedocs.io/en/latest/](https://magic-wormhole.readthedocs.io/en/latest/)  The good thing about wormhole is that it is safe to share files with strangers and the transfers are encrypted.  This isn't for on-demand, anybody, transfers. It is just to hard for that.

Allowing HTTP for file uploads is problematic from a security standpoint.  For downloads, setting up a static file website is pretty easy.  There are easy ways to share all the files in the current directory without forcing any authentication. Almost every scripting language has a short command, often 1-line, webserver.  No HTTPS/TLS however.  Good for quick stuff inside your LAN until you are used to sftp, scp, rsync.

Of course, there are always 50+ options to any problem.  You probably just want to setup the web server with Let's Encrypt TLS certs. That's the most expected.

---

### Post by ulao3 on 2024-11-10
thx for the first note!

the second "For authenticated access, use sftp." I did that but could not get the webpage to call to it? It wanted to ask the OS for the default FTP ( stupid windows) and then the browser rejected it. I changed it to use another and it rejected it. Turns out ftp / sftp is not longer usable from a hyper link in like all the main browsers?  If it is possible,  how do I do that? sftp:// seems not to work?

and yes lots of good info there I have to explore.

---

### Post by TheFu on 2024-11-11
Don't confuse web browser and file manager.  Also, I assume you are using a Linux workstation as the sftp client.  If you are using some other OS, I've heard of WinSCP and Filezilla, but haven't used either in over 15 yrs.

For my needs, I use different methods than sftp and I barely use any file managers.  I didn't mention how I do it because it would be overwhelming for anyone initially wanting to use a protocol like plain FTP which should have died in 2002 when telnet was killed (for the most part).  Plain FTP has no place in any discussion of "a secure server".

Anyway, I'm not an expert on YOUR browser or file manager.  Perhaps there are how-to guides?   [https://askubuntu.com/questions/70423/how-do-i-connect-to-a-server-with-thunar-in-xubuntu](https://askubuntu.com/questions/70423/how-do-i-connect-to-a-server-with-thunar-in-xubuntu) explains how to get Thunar to support sftp://, for example.    A little older, but the basic idea [https://www.techrepublic.com/article/how-to-use-linux-file-manager-to-connect-to-an-sftp-server/](https://www.techrepublic.com/article/how-to-use-linux-file-manager-to-connect-to-an-sftp-server/)  Did I mention that all these tools honor the ~/.ssh/config file stanzas for access?  That means you can connect using different usernames, to different IPs, using different identity ssh-keys, with different settings, if that is needed and only be prompted to unlock the ssh-key once per login on the client workstation.  It is crazy convenient to use ssh-keys.

---

