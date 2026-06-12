---
title: "WINS resolution using Ubuntu + Samba"
date: 2004-11-15
forum: General Help
---

### Post by Mumbly on 2004-11-15
I am running a Ubuntu 4.1 on a server at my work, and I am having difficulty getting the server to resolve names correctly. The connection correctly registers in WINS, as all other machines can see the server by name with no problems at all. However, Warty is restricted to only seeing names within it's own subnet, and cannot see any machines by name on the outside. Warty can see the WINS server by IP as well.

I have correctly set the WINS resolution address in smb.conf (it is correctly enabled as a client, not a server), and testparm gives no errors at all in the config. I've also disabled IPv6 from loading due to some slowness issues that have been reported. This GREATLY sped up DNS issues I was having, but did not fix my original problem. I can edit /etc/hosts to match up names to IPs, and change /etc/resolv.conf to use the host file, but that really is not a solution for me since our clients are DHCP only, and changing that IP all the time would be counter productive.

I am running backuppc on the server (it's main function), and truly need to resolve machine names in order for it to work. 

Name resolution has not been an issue really with FC2, but FC2 does not run backuppc nearly as effectively as Warty does (at least for me). Any help would be greatly appreciated. Thank you!

Wes ](*,)

---

