---
title: "Unable to login via ssh"
date: 2021-11-25
forum: General Help
---

### Post by azakero on 2021-11-25
So I have this Ubuntu 20.04 VPS which was working fine an hour back but now I am unable to login to my sudo user as well as root user. I had also disabled root login before. The sudo user also hava 2FA enabled.


When it was working, I deployed a static website and wanted to install certbot ssl via sudo user. But it was getting denied that I don't have permission. So after searching online I found something to change permission which is sudo chmod 755 and another one which sudo chown root:root. Then it worked and my website was running but then I got logged out and can't log back in. Password is correct as I already tried like a million times. After running this command:


```
ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no -p 4256 user@<ip>
```


I get Permission Denied output. 


After running ssh verbose command ssh -v user@13.210.34.26 -p 4256 I get a long list of output which is here: [https://pastebin.com/jb1YLqqS](https://pastebin.com/jb1YLqqS) 

What did I do wrong? How can I fix this? Is there a way to access my server without reinstalling the whole system? I have so many apps and data. I can't imagine of losing them. Even though I have a backup with timeshift but they are inside the server. I feel helpless here. 

I should also mention that my hosting, Namecheap, had provided me a web panel/dashboard which has these options: Reboot, Shutdown, Boot, Reinstall, VNC, Log, Power Off, Reconfigure Networking and Rescue. 


Someone please help me out. I'm posting it here cause I'm sure there are a lot of sys administrators here who can help me. Namecheap denied to help me as I got a self-managed server and I don't have cpanel. I am a noob in managing my own server. And I don't have the means to get a managed one. Someone please help me out!

---

### Post by TheFu on 2021-11-27
```
sudo chown root:root
```
isn't the complete command.  What, EXACTLY, did you enter and from which directory?

It is very possible that you have only 2 choices.
Restore from backup
or
reinstall.

/c/Users/Admin/ isn't a normal Unix location.  Which OS, exactly, is being run?  Or are you just using a non-Unix client?

Here's an ssh troubleshooting guide that might be helpful: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

BTW, you aren't the first and won't be the last to make this sort of mistake.  This is why daily, automatic, versioned, backups for everything you don't want to lose is very important. I've been an admin about 25 yrs now and need to restore a file about once every few weeks after an "oooops" moment.  Thankfully, it only takes a few really bad problems to teach most of us NOT to screw around with global changes.

The answer to my first question will tell us if this is a trivial issue, easily fixed, or time to just reinstall and be careful.
Also, if reinstalling a server and using the backup-restore is so hard, I think you are doing it wrong.  Restoring a backup for any server should be less than 45 minutes ... not counting huge amounts of data.  For for 20G of data or less, 45 min restore is easily achieved.

---

