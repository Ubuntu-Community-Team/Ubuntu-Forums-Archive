---
title: "ssh problems"
date: 2015-03-15
forum: General Help
---

### Post by Penfold1971 on 2015-03-15
A couple of years ago I got help here when setting up a home build running Ubuntu. One area I got help for was in setting up passwordless ssh-ing so that I could monitor the headless Ubuntu machine from my Macs without too much typing in Terminal. In addition someone helped me set up a short alias for the ssh-ing, so that all I had to do was type in a very short command to get into the Ubuntu machine. Lazy, I know, but so much easier than what I had been used to.
 
The Macs consist of an Intel iMac (OS 10.6.8), a G4 PowerBook (OS 10.4.11) and a G4 iMac (OS 10.4.11). Everything has been working flawlessly until today.

Now when I try to use the short alias I get the message :

```
[SIZE=2]Warning: the RSA host key for 'ubuntubox.local' differs from the key for the IP address '10.0.1.x'
Offending key for IP in /Users/intelimac/.ssh/known_hosts:2
Matching host key in /Users/intelimac/.ssh/known_hosts:3
Are you sure you want to continue connecting (yes/no)?[/SIZE]

```

Typing 'yes' gets me into the machine fine, but the warning had me spooked since I hadn't seen it before.

IN ADDITION :

Trying to ssh into, for instance, the G4 iMac from the Intel iMac gets this response :
```

Last login: Sun Mar 15 14:35:04 on ttys000
Intel-iMac:~ intelimac$ ssh g4imac@10.0.1.x
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
nn:nn:ln:ln: ln:nn:nn:nn:nn:nn:nn: ln:nn:nn:nn: ln.
Please contact your system administrator.
Add correct host key in /Users/intelimac/.ssh/known_hosts to get rid of this message.
Offending key in /Users/intelimac/.ssh/known_hosts:1
RSA host key for 10.0.1.x has changed and you have requested strict checking.
Host key verification failed.

```

I should start from scratch and set up new RSA keys. I understand that I should remove all old keys first. Is that correct?

If so,

(a) is the correct command [FONT=Courier New]rm ~/.ssh/id*[/FONT] 
and
(b) should I issue that command from Terminal on each machine separately?

Thanks in advance.

---

### Post by Lars Noodén on 2015-03-15
If the keys don't match, it is important to get to the bottom of it.  The host keys no longer match what your client remembers for that ip address (if it is not a MITM attack).  Did you either change ip addresses of the server or re-install it?   It is quite common to forget to backup/restore the SSH keys when reinstalling the server.

When you are physically at the server you can check the fingerprint of the RSA key there. 

```

ssh-keygen -lf /etc/ssh/ssh_host_rsa_key.pub

```

Then if that matches what you are getting in your warning message, you can clear the bad entry from *known_hosts* using [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html)

```

ssh-keygen -R 10.0.1.*x*

```

---

### Post by SeijiSensei on 2015-03-15
> Warning: the RSA host key for 'ubuntubox.local' differs from the key for the IP address '10.0.1.x'
Offending key for IP in /Users/intelimac/.ssh/known_hosts:2
Matching host key in /Users/intelimac/.ssh/known_hosts:3
Are you sure you want to continue connecting (yes/no)?
At some point the IP address changed for your server so that the key in line 2 of known_hosts no longer matches the machine's key.

This is almost certainly a harmless problem especially since the machine is inside your local network.  I'd just delete the lines in known_hosts and reconnect.

Your server does use a static IP address, yes? If for some reason it gets its IP from a DHCP server, you should [use static addressing instead]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html").

---

### Post by Penfold1971 on 2015-03-15
> **SeijiSensei said:**
> This is almost certainly a harmless problem especially since the machine is inside your local network.
Yes, my setup is maybe a little amateur - an AirPort Extreme Base Station sits between the modem and my computers. The Macs are connected wirelessly to the AEBS and the Ubuntu machine is connected directly to the AEBS via an ethernet cable.

  > **SeijiSensei said:**
> I'd just delete the lines in known_hosts and reconnect.
Can you give me simple instructions as to how to do this please? I have to admit I don't understand 'the lines in known_hosts'. Sorry.
> **SeijiSensei said:**
> At some point the IP address changed for your server so that the key in line 2 of known_hosts no longer matches the machine's key.
> **SeijiSensei said:**
> Your server does use a static IP address, yes?

Regarding these two quotes from your post, can you indicate what 'server' means? Is it one of my machines, or something that my ISP (Zen) operates?

You will gather that I'm an enthusiastic amateur with little technical know-how.

---

### Post by Penfold1971 on 2015-03-15
Thanks, Lars, but when I ran that command (from my Intel iMac), the result was
```
/etc/ssh/ssh_host_rsa_key.pub: No such file or directory
```
Should I run the command from the Ubuntu machine?

---

### Post by Lars Noodén on 2015-03-15
> **Penfold1971 said:**
> ...
  
Can you give me simple instructions as to how to do this please? I have to admit I don't understand 'the lines in known_hosts'....

Regarding these two quotes from your post, can you indicate what 'server' means? Is it one of my machines, or something that my ISP (Zen) operates?


In this context, the 'server' is the machine you are logging in to and the 'client' is the machine you are logging in from.  

As far as removing the offending line from *~/.ssh/known_hosts* you can dig it out manually with gedit or nano.  Or you can let [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html) do the work for you:

```

ssh-keygen -R 10.0.1.*x*

```

---

### Post by Lars Noodén on 2015-03-15
> **Penfold1971 said:**
> Thanks, Lars, but when I ran that command (from my Intel iMac), the result was
```
/etc/ssh/ssh_host_rsa_key.pub: No such file or directory
```
Should I run the command from the Ubuntu machine?

Yes.  It is for the one which is running OpenSSH-server for you.  The SSH server has keys that identify it to the client when you try to connect to it so that you know you are getting to the right machine.  When you connect the first time they get saved in *~/.ssh/known_hosts*  And later if you connect again, the client uses them to see if the server matches.  So if you are connecting *to* your Ubuntu machine, then that command should be run on it so you can verify the fingerprint.  If the one you see on the server (the Ubuntu machine) matches the one you are seeing in the warning, then everything is ok and your IP probably changed in the AEBS, which happens and is normal with DHCP.  

Note that there can be other keys floating around such as those on the 'client', the one you connect with [ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html).  Those keys are ones that you could use to identify yourself to the server.  They're not involved in the warning you're seeing.

---

### Post by Penfold1971 on 2015-03-16
Thanks for your patience.

I sat at the Ubuntu machine and in Terminal used the command :
```
ssh-keygen -R 10.0.1.x
```
where 10.0.1.x is the IPv4 address (is this the correct terminology?) of the Ubuntu machine.

When I try to connect to the Ubuntu machine from the Intel iMac, I still get the response :
```
[SIZE=2]Warning: the RSA host key for 'ubuntubox.local' differs from the key for the IP address '10.0.1.x'
Offending key for IP in /Users/intelimac/.ssh/known_hosts:2
Matching host key in /Users/intelimac/.ssh/known_hosts:3
Are you sure you want to continue connecting (yes/no)?[/SIZE]
```
I did a reboot of the Ubuntu machine, still no joy.

I'm afraid this is well over my head. I set it all up in June 2012 with a lot of help from folk here, and although I've retained the notes and details from the setting up, I have no feel for what to do when things go wrong.

Can I scrub the keys and start again? Do I need to go to each machine in turn to do this? If so, can you spell out in simple terms how I do that?

---

### Post by Lars Noodén on 2015-03-16
It's confusing with all the keys, but it can make sense when you know the pieces involved.  
The warning is saying "We're expecting key X from that ip address, because that's what we got before, but we're getting sent key Y instead.  What's up with that?"

Say you are sitting at the Intel iMac and you get the error above.  It's complaining that the public key that it ( Intel iMac ) has on record for address 10.0.1.*x* does not match what the server ( Ubuntu machine ? at 10.0.1.*x* ) is currently sending.  Either the key is off, or more likely the IP is different from when the record was first made ( Intel iMac still ) in the file */Users/intelimac/.ssh/known_hosts*, specifically on line 2 of that file.  So, at the Intel iMac, you can purge that key and start over either by editing  */Users/intelimac/.ssh/known_hosts* manually and nuking the second line or else by having 'ssh-keygen' do it for you:

```

ssh-keygen -R 10.0.1.*x*

```

But if you go sit over at the server ( 10.0.1.*x*, which is the Ubuntu machine ? ) then you can double check what RSA key ( the type mentioned in the warning ) is there by looking at that key's fingerprint and comparing it to the fingerprint shown in the warning you get over on the Intel iMac.  By sitting at the server ( 10.0.1.*x* ) you can check the RSA key's finger print with the following:

```

ssh-keygen -lf /etc/ssh/ssh_host_rsa_key.pub

```

---

### Post by Penfold1971 on 2015-03-16
I pretty much understand (I think) most of what you have told me there, Lars. Thanks again.

My problem starts when I get to :
> So, at the Intel iMac, you can purge that key and start over either by editing*/Users/intelimac/.ssh/known_hosts* manually and nuking the second line or else by having 'ssh-keygen' do it for you:
I can open and read the file ~/.ssh/known_hosts on the Intel iMac fine.
There are basically four sections in the file, corresponding to the G4 iMac, the G4 PowerBook, the Ubuntu machine and the intel iMac respectively.

After 'ubuntumachine.local, 10.0.1.x ssh-rsa' there are 372 characters, and *the same* 372 characters appear after '10.0.1.y ssh-rsa' (which is the Intel iMac).

The corresponding 372 characters for the other two machines are different to those above, and also to each other.

I don't feel confident about what to do next.

My question at this point is: Can I just somehow scrap the whole thing - delete the keys on all machines - and start afresh?

---

### Post by Lars Noodén on 2015-03-16
> **Penfold1971 said:**
> After 'ubuntumachine.local, 10.0.1.x ssh-rsa' there are 372 characters, and *the same* 372 characters appear after '10.0.1.y ssh-rsa' (which is the Intel iMac).


Those are the lines to delete if you want to start afresh.  You can do it manually in your favorite editor or else use 'ssh-keygen -R' as above, once for each address.  

However, since the RSA key is the same for both addresses, it looks like your DHCP server dealt out a new address to your Ubuntu machine, as SeijiSensei considered above.  A long term solution for that would be to have your AEBS assign fixed addresses to your machines.

---

### Post by Penfold1971 on 2015-03-16
[SIZE=3][FONT=arial]This might be best - i.e.  to scrub everything and start again.

(I know zero about how to get the AEBS to assign fixed addresses to my machines. Does that mean once one is 10.0.1.4, it will always be that? We've discovered that these things change after say we've been off-line. it might be the AEBS is getting old I suppose. Can these things get cranky with old age?)

Questions:

1)  Do I sit at each machine and carry out 'ssh-keygen -R 10.0.1.*x*' with the value of x corresponding to *that* machine?

2) Do I delete the file ~/.ssh/known_hosts ? If so, is it with the command rm  ~/.ssh/id*. I've seen that in my old notes but don't know what the 'id*' means.

3) Can I then start the whole process of assigning keys for passwordless ssh-ing all over again?

As you can tell, I have no expertise at all - it must be difficult for folk like you to shift down enough gears to communicate at my level;).[/FONT][/SIZE]

---

### Post by Lars Noodén on 2015-03-16
1) Yes, from each machine that you log in *from*, run 'ssh-keygen -R 10.0.1.x' to clear out the bad ip address - key association.  It should ask for confirmation of the 'new' key the next time you log in to the remote machine.

2a) You can leave  ~/.ssh/known_hosts  if you follow step #1 instead.  Step #1 will preserve the other keys.  
2b) You'll probably want to leave ~/.ssh/id* alone for now.  They are innocent here and how you identify your client to the server.  The current problem is coming from the other direction, identifying the server to the client.  

3) If you leave  ~/.ssh/id* untouched then you should not have to redo those steps.

---

### Post by Penfold1971 on 2015-03-16
Thanks, Lars.

I'm away from the machines now for a few days, but will check back in on Friday. This has been a bit un-nerving, so many thanks again for your help.

---

