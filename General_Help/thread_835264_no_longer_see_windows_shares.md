---
title: "no longer see windows shares"
date: 2008-06-20
forum: General Help
---

### Post by dafaltusr on 2008-06-20
Has anyone seen a problem of not being able to connect to windows shares?  It was working for the longest time and now nothing.  I am wondering if there was an update I installed that created the issue. I usually print to a windows printer and I could see shares on the same box that has the printer.  Now I see do not see anything.  Is there a fix??

Thanks

---

### Post by russlar on 2008-06-20
> **dafaltusr said:**
> Has anyone seen a problem of not being able to connect to windows shares?  It was working for the longest time and now nothing.  I am wondering if there was an update I installed that created the issue. I usually print to a windows printer and I could see shares on the same box that has the printer.  Now I see do not see anything.  Is there a fix??

Thanks

Did you recently update samba? What Windows OS are you connecting to? Have user accounts changed on the Windows side?

---

### Post by dafaltusr on 2008-06-20
This is going to sound bad, I haven't done anything to samba unless I have installed an update without thinking which is a possibility.  I am trying to get to a WIN2K box that the printer in installed on and has been working.  I did put in a new access point and changed the address scheme -- can't imagine why that would be a problem.  Rather than use 192.168.1.0/24 -- I changed to a 10.168.1.0/28.  I have tried different smb.conf configurations.  I re-installed smbclient and samba. The only thing I found was someone said the uninstalled everything and started over and it magically started working.  I hate doing that.  Once I got everything working with 8.04 I try not to add anything major.  And it had been working.

---

### Post by dafaltusr on 2008-06-20
and the user accounts have not changed. (I only use one account) I do not even see any computers on the network when I try for see the network via network selection.  I cannot remember if the Windows boxes see my linux box.  I will have to check.

---

### Post by avtolle on 2008-06-20
It seems to me that at least one, if not two, recent updates I installed (including one today) included updates to samba and related apps. This may be what is causing you the difficulty, not sure that it is, but am offering it as a suggestion.

---

### Post by wootah on 2008-06-20
> **dafaltusr said:**
> and the user accounts have not changed. (I only use one account) I do not even see any computers on the network when I try for see the network via network selection.  I cannot remember if the Windows boxes see my linux box.  I will have to check.

Perhaps an update screwed with your iptables?
```
sudo iptables -L -n
```
Check through your iptables and see if the network traffic is indeed going through.
-L  :  List all the iptables
-n  :  Avoid reverse DNS lookup (speed things up)

My outbound table is pretty restrictive, but I allow mostly everything to pass to the windows machine on the network. Perhaps by changing the ip class on your network, the firewall rules don't apply anymore?

Just a suggestion :)

PS: Firestarter helps a lot with configuration.

---

### Post by cariboo on 2008-06-20
Can you ping anything on your network?

Jim

---

### Post by dafaltusr on 2008-06-20
Thanks I tried the iptables and it is blank.  

I can ping the target.  Is there a command to search for smb devices?  I thought there was a command but for the life of me I cannot remember what is it.

---

### Post by robklg on 2008-06-20
Maybe you can try this alternative method...

If you use the 'connect to server' feature in 'Places' it sometimes doesn't work... At least for me.

But what does work for me is simply opening your home folder in nautilus... (Places -> Home Folder)

Now press Ctrl+l (or Go -> Location)

now type: smb://servername

Somehow for me it works in this way, and not through 'connect to server'.

Please try that and post your results.

---

### Post by wootah on 2008-06-20
> **dafaltusr said:**
> Thanks I tried the iptables and it is blank.  

I can ping the target.  Is there a command to search for smb devices?  I thought there was a command but for the life of me I cannot remember what is it.

smbtree is the browser I believe you are looking for. I suggest reviewing the man pages :)

---

### Post by dafaltusr on 2008-06-20
the SMB://server did not work.  If I do the smbtree command this is what I see -- 
mike@mike-laptop:~$ smbtree
Unknown parameter encountered: "domain admin group"
Ignoring unknown parameter "domain admin group"
Unknown parameter encountered: "ldap server"
Ignoring unknown parameter "ldap server"
Password: 
MIKESWORLD
	\\TLAPTOP        		
timeout connecting to 208.67.219.132:445
timeout connecting to 208.67.219.132:139
Error connecting to 208.67.219.132 (Operation already in progress)
cli_start_connection: failed to connect to TLAPTOP<20> (208.67.219.132). Error NT_STATUS_ACCESS_DENIED
	\\TERRI-XP       		
timeout connecting to 208.67.219.132:445
timeout connecting to 208.67.219.132:139
Error connecting to 208.67.219.132 (Operation already in progress)
cli_start_connection: failed to connect to TERRI-XP<20> (208.67.219.132). Error NT_STATUS_ACCESS_DENIED
	\\ARTROOM        		
timeout connecting to 208.67.219.132:445
timeout connecting to 208.67.219.132:139
Error connecting to 208.67.219.132 (Operation already in progress)
cli_start_connection: failed to connect to ARTROOM<20> (208.67.219.132). Error NT_STATUS_ACCESS_DENIED
mike@mike-laptop:~$ 

When I browse the network from the windows boxes I do not see my linux box.

Thanks

---

### Post by dafaltusr on 2008-06-21
Thank you everyone it started working but it was one of two things.  I added and entry into the hosts file to resolve the server name and I ended up re-installing samba,  I shot gunned the end.  Everyone helped point me in the direction.  Really appreciate everyone's help. 

Thanks

Mike

---

### Post by thndrbck on 2008-06-21
I just went through the same thing. I tried reinstalling samba and smbclient, but still no joy. Then, noticed that synaptic didn't want to open. That has been a problem recently, and it has been because the hosts file doesn't have the host name by itself.

I opened the /etc/hosts file, added the host name right after the 127.0.0.1 entry, before the host.workgroup entry.

After that, the shares reappeared.

---

### Post by Valir on 2008-06-21
Hi, 

I had the same problem. 

My /etc/hosts looked like this

127.0.0.1 localhost
127.0.1.1 [myhostname]
....

I edited it:

```
sudo gedit /etc/hosts
``` 

After 127.0.0.1 I put my hosts name and the domain name of the windowsshare:

```
127.0.0.1 myhostname.MSHOME
```

Then I deleted the 127.0.1.1 line.

That seems to work for me.

---

### Post by dafaltusr on 2008-06-21
I changed this line in the smb.conf

   name resolve order = bcast lmhosts host wins 

bcast was last and I moved it first.  I helped also.

thanks again

Mike

---

### Post by cariboo on 2008-06-21
You can also try smbclient:

```
smbclient -L <hostname> -U <user> -P <apssword>
```

I can't do it on this particular computer as I just reinstalled intrepid and I haven't finished setting it up yet.

Jim

---

