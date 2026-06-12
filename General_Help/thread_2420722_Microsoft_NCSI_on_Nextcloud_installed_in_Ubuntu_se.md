---
title: "Microsoft NCSI on Nextcloud installed in Ubuntu server 18.04?"
date: 2019-06-09
forum: General Help
---

### Post by almedina on 2019-06-09
Hi guys, I'm very worry about something, I have Logwatch in ubuntu server 18.04 to send email notifications once a day, for my surprise I discover the following information.

[FONT=Arial]  /script: 1 Time(s)[/FONT]
[FONT=Arial]       /sdk: 1 Time(s)[/FONT]
[FONT=Arial]       /sqlite/main.php: 1 Time(s)[/FONT]
[FONT=Arial]       /sqlitemanager/main.php: 1 Time(s)[/FONT]
[FONT=Arial]       /test/sqlite/SQLiteManager-1.[/FONT][FONT=Arial]2.0/SQLiteMan ... -1.2.0/main.php: 1 Time(s)[/FONT]
[FONT=Arial]       [/FONT][http://www.msftncsi.com/ncsi.txt](http://www.msftncsi.com/ncsi.txt)[FONT=Arial]: 1 Time(s)[/FONT]
[FONT=Arial]    408 Request Timeout[/FONT]
[FONT=Arial]       null: 1 Time(s)

[/FONT]Why a Microsoft utility is trying to run on a Linux server?, it doesn't have a sense for me, when I open the link it shows me the following: ( [COLOR=#000000]Microsoft NCSI ), any help is very welcome and thanks in advance.[/COLOR]

---

### Post by TheFu on 2019-06-10
Logwatch is nice.  I review reports daily for all my systems.

That is a hacker trying to figure out what your nextcloud system is running. I would guess that ncsi has a remote exploit that they want to use, but the script hitting your server is broken.

Leaving nextcloud available to parts of the internet where you don't need access is not a best practice.  If you can, the best practice is to not put nextcloud directly on the internet, rather, require the use of a VPN to access the network.  

My nextcloud server is available without a VPN only on the local network.  From the internet, I have to start a VPN to access it.  When you do that, only allowed clients will connect and your logs for strange attempts will be empty.  The VPN enables all sorts of other great tools too and works from pretty much any networked client. On android, a VPN is easier. On a laptop, the VPN also works, but I tend to use an ssh proxy tunnel instead. I find ssh more convenient since I can script commonly used access needs.

If those are your only log file entries, that's pretty tame.  If this machine is left internet-facing, soon there will 10,000 weird entries in the logs daily. Hopefully, nobody will hack in and pwn your box and network.

---

