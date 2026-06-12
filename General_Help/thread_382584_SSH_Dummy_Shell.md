---
title: "SSH Dummy Shell"
date: 2007-03-12
forum: General Help
---

### Post by bobpaul on 2007-03-12
I have a limited user account that I allow others to connect to via ssh strictly for tunneling purposes--I use it as a way to securely tunnel back to their machines for support via VNC.

I have that user configured with a null password and key authentication. I've tried setting the users shell to something like /dev/null or /bin/false, but remote connections are either refused or terminated immediately.

Via Google I've found manpages for a tool "ssh-dummy-shell" to appears to be available for commercial Unixes. When executed it waits for a keystroke and then exits. When set as a shell, it has the effect of allowing the session to remain active--for scp/sftp transfers or port tunneling--until a key is pressed.

Does anyone know of something like this for Linux, or ideally tested with Ubuntu?

---

### Post by schilcha on 2007-03-12
Have a look at rbash, which does not what you want to, but it's better than plain bash

---

### Post by schilcha on 2007-03-12
Another suggestion:

Write your own shell:
```

#!/bin/bash
bash -r -c read

```
save it as e.g. "/bin/ssh-dummy-shell" and add the line "/bin/ssh-dummy-shell" to the file /ets/shells
Dont forget to set execute-permission to all users (chmod a+x).

That new shell seems to behave just like you want (just exist and do nothing until the user hits enter).

Good Luck!

---

### Post by bobpaul on 2007-03-12
> **schilcha said:**
> Another suggestion:

Write your own shell:
...
That new shell seems to behave just like you want (just exist and do nothing until the user hits enter).

Good Luck!

Oh, that seems too simple! I assumed I'd have to break out some heavy man pages and learn how to code a shell to do this myself! Thanks much! Worked great!

---

### Post by wisi on 2007-04-04
> **schilcha said:**
> Another suggestion:

Write your own shell:
```

#!/bin/bash
bash -r -c read

```
save it as e.g. "/bin/ssh-dummy-shell" and add the line "/bin/ssh-dummy-shell" to the file /ets/shells
Dont forget to set execute-permission to all users (chmod a+x).

That new shell seems to behave just like you want (just exist and do nothing until the user hits enter).

Good Luck!

My purpose is : allow a user only useing sftp to transfer files but do not allow he login via ssh.

I try this scipt ssh-dummy-shell. It does work for ssh tunneling, but it does NOT work for a sftp only purpose.
I try to change the user's shell to /bin/false or /bin/nologin, but it can not use sftp either.
Then I try to chang it to /bin/rbash,but it can simply get a full function bash just type the command "bash" in rbash shell.
So please help me to resolve this problem. Thanks in advance.

---

### Post by Maverick88 on 2007-04-19
Thanks for the info in this post.  I have always had one nagging question when working with SSH.

I understand many users create a dummy account solely for SSH tunneling purposes.  What is the advantage of that espcielly when the tunnel is available to ALL users after the tunnel is set up?   

Are there security advantages? 

 (But if you set up the SSH config file properly, one would normally disable normal logins/password and only accept SSH generated keys).

I just can't see any advantages.  What am I missing?

Rob

---

### Post by stylishpants on 2007-04-19
scponly is another option.

fraser@ged:~$ apt-cache show scponly
Package: scponly
Section: universe/utils
<snip>
Description: Restricts the commands available to scp- and sftp-users
 "scponly" is an alternative 'shell' (of sorts) for system
 administrators who would like to provide access to remote users to
 both read and write local files without providing any remote
 execution priviledges.  Functionally, it is best described as a
 wrapper to the mostly trusted suite of ssh applications.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by bobpaul on 2007-04-19
> **Maverick88 said:**
> Thanks for the info in this post.  I have always had one nagging question when working with SSH.

I understand many users create a dummy account solely for SSH tunneling purposes.  What is the advantage of that espcielly when the tunnel is available to ALL users after the tunnel is set up? 

The tunnel isn't any more secure, but I'm not going to give my grandpa a key to access my personal account on the machine. My account has sudo privileges, and all of my files. But, I will give him a setup.exe that installs Putty and VNC Server, configures VNC Server to only allow connections from Localhost and populate putty with a connection back to my computer with remote port forwarding enabled restricted to the local machine.

With that, he can fire up putty and double click the connection without worrying about how to set it up. When he logs in, the dummy shell for the vnc-viewer account I created says "Minimize this window. Pressing [Enter] terminates the connection" At that point I, or anyone else using my machine--so that'd be just me then--can access his VNC by connecting to localhost:port. He doesn't need to have port forwarding for VNC to work, and we can both feel better about not using VNC directly over the internet. I also feel happy because I know he doesn't have any shell access that he /might/ be able to screw something up with.

The dummy shell is not for the benefit of the connection being tunneled, but to allow only the amount of access required. You wouldn't give your entire key ring to someone who's going to water your plants for the weekend; they don't need your safety deposit box key. Likewise, I'm not going to give shell access to my grandpa when he only needs to forward a ports. Sure, he could forward extra ports if he knew how, but I trust him enough to give him my house key and water my plants, he just can't have all my keys.

---

### Post by dannyboy79 on 2007-04-19
this is exactly what I was looking for. except I don't need the special bash with restricted privalages, i just really want to setup a ssh tunnel to allow vnc thru it. here's the deal. i work on computers on the side, i have recently gotten a guys compouter back up and running win2000 pro. i told him he should try out linux. I installed a dual boot with Xubuntu Edgy, i installed ssh and vnc. i however am not sure how to integrate them? the vnc is x11vnc I am pretty, it uses port 5900. i setup his iptables to only allow ssh and vnc thru. his setup when he takes his computer home is computer>>cable modem>>internet. So I didn't need to setup samba, nfs or any other services. My couple of questions are as follows:

1.) I am a little confussed on public/private key pairs. I have them working properly on my own xubunutu laptop as well as my Ubuntu Desktop/Server but when I tried adding his id_rsa to my authorized_keys file within ~/.ssh/ I couldn't get it to work. Could you maybe explain how I am to utilize a private key from another computer? So right now my current authorized keys file on xubuntu has ubuntu pub key in it, my ubuntu authorized keys file has xubuntu pub key file. then I have the private key for each of the other computers stored within ~/.ssh/ named id_rsa. Am I doing something wrong?

2) I would like to not have port 5900 open on his machine since he doesn't have a hardware firewall, if I just left open port 22 (ssh) could I just ssh in, and hten do this thing about starting a vncserver on the localhost or whatever? I am not sure what I need to do or how to tell you what I need to do but this is what I'd like to be able to do. (SORRY SO CONFUSSING)
     2a. I would like to leave open port 22 and that's it, obviously I need to learn hopefully from you, how to get the pub/private key to work so his machine doesn't get hit with dictionary attacks all day. Then can I somehow ssh into his box using pub/priv authentification and somehow start a vncserver, that I can somehow connect to it tunneled thru ssh? I would like to learn how to do this using windows xp pro as well as when I am using my ubuntu machine. Or do I need to do it the other way and setup this special shell so he can ssh into my box, then click on an icon which will start a vnc server on my machine allowing me to connect to localhost which is actually his machine??? See I don't understand really sorry. 

Thank you if you can help.

---

### Post by Maverick88 on 2007-04-19
Many thanks for the reply to my question.  

Let me see whether I understand what you are doing.  A VNC Server is running on your Dad's computer.  And a SSH server is running on your computer.  You Dad uses Putty to connect to your SSH server (via dummy account) and create a REVERSE SSH Tunnel back to his computer.

e.g.  ssh [email]dummy@mycomputer.com[/email] -R 5900:127.0.0.1:5900

Then you run a VNC Viewer, connect to localhost and take over your Dad's computer.

(FYI -- This approach is also described on macosxhints for mac users -- see [http://www.macosxhints.com/article.php?story=20050429153115383](http://www.macosxhints.com/article.php?story=20050429153115383).  The same approach will work on Linux).

But since a reverse SSH tunnel is created, how can your Dad access your computer?  I thought only you could access your Dad's computer via the reverse tunnel.  (If that is the case, I don't see the security risk).

Or does the SSH tunnel once created work both ways?

Rob

---

### Post by bobpaul on 2007-04-19
> **Maverick88 said:**
> Many thanks for the reply to my question.  

e.g.  ssh [email]dummy@mycomputer.com[/email] -R 5900:127.0.0.1:5900

Then you run a VNC Viewer, connect to localhost and take over your Dad's computer.
...

That command is exactly what I'm having my Grandpa do with putty, but that will also result in a shell. SSH will *always* provide a shell for the user or else terminate immediately (thus closing the tunnel), as well as any tunneling you also request. I don't want to give my Grandpa shell access, but I also want to keep the tunnel open. By using the dummy-shell, when he logs in he doesn't get a usable shell (just a comment) and the connection remains open until he presses enter or closes the terminal window. If you're still confused I'd suggest you duplicate the setup on your home computer so that you can see the difference in behavior. Just substitute mycomputer.com with localhost.

---

### Post by bobpaul on 2007-04-19
> **dannyboy79 said:**
>  Snip 

First of, your questions are off topic. The thole thread is about restricted shell, but you're here now so I'm not going to make you go to another thread. Just try not to do it frequently, as it muddies up the thread for new users looking for their fix. At least you came after the problem was solved.

Secondly, you should never use VNC over the internet without tunneling it through ssh. VNC essentially sends raw JPG screen captures and keystrokes as clear text. Not wise. Also VNC generally uses short passwords, also sent cleartext, AFAIK.

> **dannyboy79 said:**
> i just really want to setup a ssh tunnel to allow vnc thru it. here's the deal. i work on computers on the side, i have recently gotten a guys compouter back up and running win2000 pro. i told him he should try out linux. I installed a dual boot with Xubuntu Edgy, i installed ssh and vnc. i however am not sure how to integrate them? the vnc is x11vnc I am pretty, it uses port 5900. i setup his iptables to only allow ssh and vnc thru. his setup when he takes his computer home is computer>>cable modem>>internet. So I didn't need to setup samba, nfs or any other services. My couple of questions are as follows:

I would setup IPTables to disallow VNC. That's the whole point of SSH in this instance. Also, are you just doing this on Xubuntu, or on Win2000 as well? It actually sounds like you'll be doing the opposite of me as you're connecting to him with SSH instead of having him connect to you.

> **dannyboy79 said:**
> 1.) I am a little confussed on public/private key pairs. I have them working properly on my own xubunutu laptop as well as my Ubuntu Desktop/Server but when I tried adding his id_rsa to my authorized_keys file within ~/.ssh/ I couldn't get it to work. Could you maybe explain how I am to utilize a private key from another computer? So right now my current authorized keys file on xubuntu has ubuntu pub key in it, my ubuntu authorized keys file has xubuntu pub key file. then I have the private key for each of the other computers stored within ~/.ssh/ named id_rsa. Am I doing something wrong?

If you're connecting to HIM, you want to put your public key in HIS authorized_keys.  You should not transfer your private key anywhere. Private keys stay on your computer, public keys go on computers you want to connect to without needing a password. Do this and you will be able to connect to him without a password and get shell access. Google "ssh no password" for more help.

> **dannyboy79 said:**
> 
2) I would like to not have port 5900 open on his machine since he doesn't have a hardware firewall, if I just left open port 22 (ssh) could I just ssh in, and hten do this thing about starting a vncserver on the localhost or whatever? I am not sure what I need to do or how to tell you what I need to do but this is what I'd like to be able to do. (SORRY SO CONFUSSING)
...

Once you have the pubkey access working, disable passwords by editing his /etc/ssh/sshd_config file. Set PasswordAuthentication and UsePAM to no.

Now, connect using ```
$ ssh username$friends_IP -L5901:localhost:5900
```
Notice I used 5901 as the localport and not 5900. If you're not running VNC server on your PC, you can use 5900 for both. If you are, though, that port will already be in use. Please see ```
man ssh
``` for more info.

Now you can hit Alt+F2 and type "vncviewer localhost:1" Vncviewer is a little weird and doesn't accept a port as a parameter. Instead it takes a "VNC screen number." The actual port VNC connects to is 5900+screen#, so in this case it will connect to port 5901 on the local machine (your ssh client) and thus port 5900 on your friends machine. ```
man vncviewer
``` should help with any questions in this step.

---

### Post by dannyboy79 on 2007-04-20
> **bobpaul said:**
>  First of, your questions are off topic. The thole thread is about restricted shell, but you're here now so I'm not going to make you go to another thread. Just try not to do it frequently, as it muddies up the thread for new users looking for their fix. At least you came after the problem was solved.. 
Ok sorry, I won't do this in the future but I figured the main reason for the dummy shell is related to my quesitons. 

> **bobpaul said:**
>  Secondly, you should never use VNC over the internet without tunneling it through ssh. VNC essentially sends raw JPG screen captures and keystrokes as clear text. Not wise. Also VNC generally uses short passwords, also sent cleartext, AFAIK...   
Thank you for your answers however I have a few cleanup questions below.

I would like to point out that according to here ([http://www.tightvnc.com/faq.html](http://www.tightvnc.com/faq.html)) the password is encrypted but the traffic after that isn't. I know it's not secure and that;s why I am asking how you're doing what you're doing but isn't the only way someone would be able to see the traffic is if they did a man in the middle?? That;s off topic so I;ll understand if you don't answer, it's just that now that I have someones attention I figured I'd ask.

> **bobpaul said:**
>  I would setup IPTables to disallow VNC. That's the whole point of SSH in this instance. Also, are you just doing this on Xubuntu, or on Win2000 as well? It actually sounds like you'll be doing the opposite of me as you're connecting to him with SSH instead of having him connect to you.  
I will be doing this ssh/vnc tunnel from both Windows XP Pro and Ubuntu. So can I use tightvncviewer within xp pro just like you're saying to use vncviewer in ubuntu?
The whole reason i am asking is so that I can block vnc port 5900 etc etc and only allow ssh, port 22. I don't use a different port because some places I want to connect from, block outbound traffic from all ports except the common ones. 20-21, 22, 80, etc etc. Also, I always make sure I use the smartest smartest passwords. Combination of upper/lower case letters with numbers and punctuation etc etc. I looked once to find out how long it would take a password I created to be cracked by brute force and it was over 20 years so I am very confident about my password selection even when people start brute forcing me which they do almost daily.

> **bobpaul said:**
>  If you're connecting to HIM, you want to put your public key in HIS authorized_keys.  You should not transfer your private key anywhere. Private keys stay on your computer, public keys go on computers you want to connect to without needing a password. Do this and you will be able to connect to him without a password and get shell access. Google "ssh no password" for more help. 
I have to take my private key with me, otherwise how would I connect from other locations? Library, work, friends house etc etc. My point is that if I can ssh into my box (or his for that matter) from anywhere I can do this trick of tunneling a brand new vnc session, is that correct?That way I can admin the pc thru a gui instead of a shell. 
Ok I think I have been misunderstanding the public/private keys thing. I thought I need to create the key pair on the particular machine that I wanted to connect to but apparently that's not the case. If I create a key pair on my ubuntu machine than I basically put the id_rsa.pub into the authorized_keys file and leave the private key there, correct? Then I also take that same id_rsa.pub file that I created within my ubuntu machine and put that inside the authorized_keyts file on all the machines I want to connect to within the usernames .ssh folder that I'll be connnecting as. BUt I also need to take the private key with for when I want to ssh into my box from off site locations correct? Well what about when I want to connect from my internal lan xubuntu machine? Do i put the id_rsa within the ~/.ssh folder on that machine also or is it more secure to call for the private key when I use the ssh command? That's my whole issue???? I am sorry that I confussed, please be patient with me. Then how do I handle that when I need 2 different key pairs? one with a  passphrase and one without a passphrase????? I know this isn't secure but I am also trying to incorporate NXServer on this guys computer which doesn't allow passphrase keys. I want to try the Nxserver as well as the tunneled vnc to see whichever one is faster, then that's what I'll use for gui admin stuff. I am going to go out on a limb and say that NXserver will be faster cause I have used both in the  past but I am having problems with the nxserver setup and public/private key authentification which is why I am trying to also get this vnc tunneled thru ssh setup in the mean time. You don't need to help with the NXserver setup as I know there are threads already for that, but my main question is how to store/handle key pairs when 1 has a passphrase and 1 doesn't? Thank you if you can answer this.



> **bobpaul said:**
>  Once you have the pubkey access working, disable passwords by editing his /etc/ssh/sshd_config file. Set PasswordAuthentication and UsePAM to no..  
Yes, thank you. i also disabled root login and add the allowusers option.

> **bobpaul said:**
>  Now, connect using ```
$ ssh username$friends_IP -L5901:localhost:5900
```
Notice I used 5901 as the localport and not 5900. If you're not running VNC server on your PC, you can use 5900 for both. If you are, though, that port will already be in use. Please see ```
man ssh
``` for more info.  Is that a dollar sign instead of an "at" symbol between the username and the ip?? So that's what I would use to connect when I am sitting at my  ubuntu machine, but what about when using putty thru windows xp pro??? Plus, I don't really understand how this starts the vncserver? Are you saying that I should leave the vnc server installed and running on his machine, but just block the ports thru iptables that it uses, like 5900 and 5901? Also, I enabled XDMCP, is that really only for remote logging in? The only real reason I am setting this up is so that a customer can call me and say, hey I need help, so he would already be logged in so I wouldn't need xdmcp correct? i setup auto login also just to inform you. I know again that this is not the safest but there are no other users in the house and I am sure he is either going to have his computer on running win2000 pro or this xubuntu edgy install I did.


> **bobpaul said:**
>  Now you can hit Alt+F2 and type "vncviewer localhost:1" Vncviewer is a little weird and doesn't accept a port as a parameter. Instead it takes a "VNC screen number." The actual port VNC connects to is 5900+screen#, so in this case it will connect to port 5901 on the local machine (your ssh client) and thus port 5900 on your friends machine. ```
man vncviewer
``` should help with any questions in this step.
Again this is for when I am in Ubuntu, what about when I am in windows xp pro? I read the man pages but i am not sure about the tunneling portion which is why I am asking. thank you very much for your help and I hope you can just answer these few more questions.

---

### Post by Maverick88 on 2007-04-20
I suspect the only security risk lies with you father changing the SSH command so that a regular SSH tunnel is created (and not a reverse SSH tunnel).

Fathers can be real hackers!  :) 

Rob

---

### Post by bobpaul on 2007-04-20
> **dannyboy79 said:**
> 
I would like to point out that according to here ([http://www.tightvnc.com/faq.html](http://www.tightvnc.com/faq.html)) the password is encrypted but the traffic after that isn't.

At least on windows, its a 3DES encryption with a static key and only accepts the first 8 characters of password. You can enter a longer password, but it's not saved or transmitted for verification.

> **dannyboy79 said:**
> but isn't the only way someone would be able to see the traffic is if they did a man in the middle?

No. Anyone with a computer on your broadcast domain has access. If you plug from a computer to a hub to the internet, then any other computer connected to that hub can run Wireshark (ethereal) or similar. This could happen at your location, the remote location, or anywhere along the line. A man in the middle occurs where you think you're authenticating with the remote host, but it's really the middle man. The remote host thinks it's allowing you in, but it's really the middle man. At least that's my understanding of the definitions. Suffice to say that beating SSH is possible, but it's difficult. Beating raw VNC is trivial.
 
> **dannyboy79 said:**
> I will be doing this ssh/vnc tunnel from both Windows XP Pro and Ubuntu. So can I use tightvncviewer within xp pro just like you're saying to use vncviewer in ubuntu?
Yes. You will need to install Putty to create the ssh session to the remote host and puttygen to convert the private key you made on unix to a private key putty can understand. The WinSCP package has that tool included.

> **dannyboy79 said:**
> The whole reason ...do almost daily. Don't care :D

> **dannyboy79 said:**
> I have to take my private key with me, otherwise how would I connect from other locations? ...
Yes. Let me rephrase. You should not give your private keys to anyone. They should stay entirely within your control. The private key stays on the client PC and the public key goes on the server (the remote pc).

> **dannyboy79 said:**
> Ok I think I have been misunderstanding the public/private keys thing. I thought I need to create the key pair on the particular machine that I wanted to connect to but apparently that's not the case.  No
> **dannyboy79 said:**
> If I create a key pair on my ubuntu machine than I basically put the id_rsa.pub into the authorized_keys file and leave the private key there, correct?
There is no need to put the public key in your own authorized_keys unless you want to connect to yourself, ie *ssh me@localhost*

> **dannyboy79 said:**
>  Then I also take that same id_rsa.pub file that I created within my ubuntu machine and put that inside the authorized_keyts file on all the machines I want to connect to within the usernames .ssh folder that I'll be connnecting as. 
That is correct.

> **dannyboy79 said:**
> But I also need to take the private key with for when I want to ssh into my box from off site locations correct?
That, or you need to create a new keypair on that other machine and put the new pub also in authorized_keys on the server. If you own a desktop and a laptop, I would create a keypair for each and pub the pubkeys in authorized. If you also want to connect from the library, friends houses, etc then you should create a third keypair and store the pub/private keys on a USB stick or something and put that in the authorized_keys on the server. Technically, if you have the private key you can use the ssh-keygen tool to re-produce the pubkey, but it's probably easiest to just hold on to both.

Well what about when I want to connect from my internal lan xubuntu machine? Do i put the id_rsa within the ~/.ssh folder on that machine also or is it more secure to call for the private key when I use the ssh command? That's my whole issue???? I am sorry that I confussed, please be patient with me. 
> **dannyboy79 said:**
> Then how do I handle that when I need 2 different key pairs? one with a  passphrase and one without a passphrase?????  I never use passphases in my keys because I don't believe my keyfiles will ever be stolen. If I had a key on a USB stick, I would definately passphrase that. Passphrases don't secure the connection anymore, they just help assure you're the only one who can use the key. If my desktop/laptop are stolen, I have bigger concerns than whether my keys are safe. ;)

If you want a second key, you can tell ssh-keygen to store to a file other than the default, and then use the **-i** parameter to specify the identity. If you do not supply that parameter, then ssh will use ~/.ssh/id_rsa, ~/.ssh/id_dsa, or ~/.ssh/identity

I don't have any experience with NXServer. I always use VNC to connect to existing sessions, such as when someone is using the computer and we need to share workspace. FreeNX can't do that, AFAIK.
 
> **dannyboy79 said:**
>  Is that a dollar sign instead of an "at" symbol between the username and the ip?? Sorry, that's a typo. It should be an '@' not a '$'

I'm going to attempt to quickly overview the setup you need.
[LIST=1]
[*]Generate a keypair on all client PCs, win/linux or copy that keypair to all machines. Putty uses a different fileformat, so use putty-gen on windows to convert
[*]Place the public key(s) on the server pc you wish to connect to in ~/.ssh/authorized_keys, 1 key per line
[*]use iptables to block port 5900. If the server is Win2k running tightvnc server and OpenSSH for windows or FreeSSHd, then configure tightvnc server to only allow local connections. It's a checkbox.
[*]from the client, connect using SSH and portforwarding. The destination of the port forward must be localhost:5900. The source port should probably be 5900 or 5901
[*]You will get a remote terminal. Minimize or otherwise ignore it.
[*]Open VNC Viewer and connect to localhost minding your portforwards.
[/LIST]

For connecting from a windows client, please see [this thread]("http://ubuntuforums.org/showthread.php?t=11808")

---

### Post by bobpaul on 2007-04-20
> **Maverick88 said:**
> I suspect the only security risk lies with you father changing the SSH command so that a regular SSH tunnel is created (and not a reverse SSH tunnel).

Fathers can be real hackers!  :) 

Rob

Right. I'll never be able to control the tunnels, but I can at least prevent him from accessing the shell.

---

### Post by dannyboy79 on 2007-04-22
bobpaul, im doing exactly what you're saying about putty portforwarding localhost:5900 which gets me a terminal onto  his box and then I open tightvncviewer and type in localhost:5900 and it states it can't connect to server. i've also tried using the opposite

I don't understand how this can work? the vnc server is still running on his machine at port 5900. im sorry if I am not understanding something here but this is exactly why I am asking. i don't understand how this can work, or I should say i don't understand how it works because I don't understand what's attempting to occur? do i need to  forward any ports on my router? I made sure my firewall on xp is letting thru 5900 and 5901. thank for anymore help you can provide.

[[IMG]http://img242.imageshack.us/img242/3222/puttyportforwardau4.th.png[/IMG]](http://img242.imageshack.us/my.php?image=puttyportforwardau4.png)

---

### Post by bobpaul on 2007-04-23
> **dannyboy79 said:**
> 
[[IMG]http://img242.imageshack.us/img242/3222/puttyportforwardau4.th.png[/IMG]](http://img242.imageshack.us/my.php?image=puttyportforwardau4.png)

Uncheck the box "Local ports accept connections from other hosts." That is unneeded could be a security risk. Also, you don't need to open your XP firewall. The next paragraph might help explain why this check box is neither needed nor desired.

The way this works is that putty listens to port 5901 on your local computer. Anything that connects to 5901 from the local computer will run across the SSH session to the remote computer where it will connect to "localhost:5900." Localhost on the remote computer is what the remote computer would call localhost, or the remote computer. This is why 5900 does not need to be opened on the firewall, because other than SSH, all of the connections are taking place locally. (From your local tightvnc viewer app to local putty app, then from your friend's local SSH server to friend's local vncserver.)

Now, your problem is two fold. You're telling putty to listen on port 5901 but you attempted to have tightvnc connect to localhost:5900, but I think you did that wrong, too. You have 3 options.
[LIST=1]
[*]In TightVNC, connect "localhost:1" which means connect to display #1 or port 5901
[*]In TightVNC connect to "localhost::5901" which means connect to port 5901
[*]Tell putty to use a source port (local port) of 5900 and just tell tightvnc to connect to "localhost"
[/LIST]

The reason I said to use port 5901 was in case you're running a VNC server on your localmachine, which is very likely the case if you're using a linux client to connect.

---

### Post by dannyboy79 on 2007-04-23
ok, to make sure I understand what you're saying.

I do have the putty configuration correct. Except you think I should uncheck that one box which allows local ports to accept connections from other hosts, i can try that but would that make this not work for sure? I'll try it no matter what.

I have tried each and every one of the suggestions that you have made. In tightvncviewer I have tried the following connections

localhost:0
locahost:1
locahost:5900
locahost:5901

Everytime I get an error saying, can not connect to server. So are you sure that my putty port forwarding is correct? There is a vncserver running on the remote machine on port 5900, I know that for sure. I have blocked all connections to the machine except thru port 22.


I don't know what else to do. What could be causeing this to not work? Do you maybe want to see my x11vnc file located within /etc/xinetd.d/. MAybe that isn't allowing connections to it's loopback? The firewall is allowing connections from localhost (loopback) so I know that's not the issue. Anymore help would be great as I would like to use a secure vnc session.

---

### Post by bobpaul on 2007-04-25
> **dannyboy79 said:**
> ok, to make sure I understand what you're saying.

I do have the putty configuration correct. Except you think I should uncheck that one box which allows local ports to accept connections from other hosts, i can try that but would that make this not work for sure? I'll try it no matter what.

Unchecking that box would neither help nor hinder this effort. What it would allow is someone else on the same LAN as your putty to use the tunnel. Since you're running TightVNCViewer and Putty on the same machine, there's no reason to have this box checked.

> **dannyboy79 said:**
> I have tried each and every one of the suggestions that you have made. In tightvncviewer I have tried the following connections

localhost:0
locahost:1

Looks good, not sure why it's not working
> **dannyboy79 said:**
> locahost:5900
locahost:5901
Neither of these will work. These equate to ports 5900+5900=11800 and 5900+5901=11801. You would want to try localhost::5901. Notice the double ":"s? That tells TightVNC to use port and not 5900+"Screen Number"


You're issue is one of the following things:
a) Putty is not connected successfully. I doubt this is the case, but make sure you have an active shell to the remote box. Try a command like "ls" to ensure the shell is active. DO NOT close the shell, just minimize it or otherwise ignore it.
b) The port forward is not active. Based on your image this does not appear to be the case, provided you clicked open (and not cancel) and succeed with a).
c) The local port is already in use and cannot be acquired by putty. This can happen if another program--such as tightvnc server--is already using the localport. I think you usually get an error, but I just tried it and didn't see such an error, so maybe not always.
d) Something is blocking loopback connections on either the client or remote box. Check that iptables is configured properly on the remote host and that a 3rd party firewall isn't blocking it on the localhost.
e) x11vnc is not allowing loopback connections. I'm not sure if this is possible, but I know tightvnc server for windows can be set to disallow loopbacks, so maybe.

To sort of test b), on the client you can check if the port is active by typing "netstate -a" into a cmd window. One of the lines should read:
```
TCP    MACHINENAME:5901  MACHINENAME:0      LISTENING
```
where 5901 is the localport you told putty to forward. This will tell you that putty is listening--or something else--is listening on that port.

To test d) and e) disable any third party firewalls and AV on the client. On the remote end, you can sit at the machine and attempt the command "vncviewer localhost" in a term window. If it asks you for a password, enter it. It should connect and show the current screen. Since it is the current screen, it'll look like one of those endless reflections of two mirrors.

My guess is either D or E is the problem. My gut would say iptables on the remote host, but if you didn't allow loopback then X should fail to start and a lot of other problems as well.

BTW, you've officially hijacked the thread :)
**Edit:** I'm in Central US timezone. Perhaps we could use IM or something like GoogleTalk voice chat to finish this if the above didn't help anything. PM me if you want to try that and we can setup a time when we're both home. Ordinarily I wouldn't offer, but this one is kind of driving me nuts, too. This has been a daily activity for me over the last 2 or 3 years.

---

