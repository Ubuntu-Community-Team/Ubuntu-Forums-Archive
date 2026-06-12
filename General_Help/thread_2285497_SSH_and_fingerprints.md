---
title: "SSH and fingerprints"
date: 2015-07-06
forum: General Help
---

### Post by zyberwoof on 2015-07-06
I've got 2 machines, Alpha and Bravo.  Alpha uses rsync to backup to Bravo over SSH via the IP address (not hostname).  This is scripted and works fine.

Alpha is a known host to Bravo, and thus doesn't require a password.  This allows the backup script to work without being prompted for a password.  This part works fine as well.

Bravo is located offsite somewhere that the WAN IP address changes every once in a while.  Usually after a power outage.  Getting this IP address isn't an issue, and I have that part automated just fine.  The issue is that each time Bravo gets a new IP address, I get prompted with something like:
```
RSA key fingerprint is xx:xx:xx:..:xx.
Are you sure you want to continue connecting (yes/no)?
```

This requires me to run the command manually once and type in yes.  After that the script works fine until the next IP address change.

Is there an easy option for me to use with SSH that would allow me to specify the fingerprint so that I'm not prompted?  Something like:
```
ssh -h 1.2.3.4 --fingerprint xx:xx:xx:..:xx
```

If not, is there another good option?  I don't want to globally ignore these on Alpha.  Just in this one case where I already know the IP address and I trust Bravo.

---

### Post by nerdtron on 2015-07-06
You can add an ssh option to skip the "strict host checking" which causes ssh to prompt when a user has a different IP.

```
ssh -o StrictHostKeyChecking=no /source/folders/ x.x.x.x:/destination/folder/ 
```

on rsync, you can add the ssh option using the following -e syntax:
```
 rsync -avh -e "ssh -o StrictHostKeyChecking=no" /source/folders x.x.x.x:/destination/folder 
```

---

### Post by zyberwoof on 2015-07-06
That looks like a good plan B.  But wouldn't that open me up to a man in the middle attack?  Is there a way to have Alpha specify who I expect Bravo to be?

---

### Post by nerdtron on 2015-07-06
But you said Bravo changes IP address. That's exactly how man in the middle attacks works, where they masquerade as Bravo but with different IP address. That is why Alpha asks you to verify Bravo, since the IP changed, the key mapping also changed. Alpha is skeptical since the remote IP changed.

---

### Post by zyberwoof on 2015-07-06
Ok.  I used a guide similar to this a while back to setup the passwordless connection: [http://linuxconfig.org/passwordless-ssh](http://linuxconfig.org/passwordless-ssh)

I'm under the impression that if I was using a password that someone could spoof Bravo.  Would someone be able to spoof Bravo or be a man in the middle since I am not using a traditional password?  (I apologize if any of my terminology is off)

---

### Post by nerdtron on 2015-07-06
Using key-based authentication is definitely safer than using password. we'll, assuming you don't have any other copies of the key except on the server themselves.
You can even make an account that doesn't have any password. An account with no password can't be logged-in but ssh keys can be used to login these type of account.

And back to the question,
> Would someone be able to spoof Bravo or be a man in the middle since I am not using a traditional password? 
No. even if somebody intercepts the traffic, if they don't have the unique ssh key pair, private and public key, they won't be able to spoof/decrypt anything. SSH keys are very secure and unique especially if you used a high encryption bit when you generated them.

---

### Post by zyberwoof on 2015-07-07
My questions have all been answered.  I appreciate you sharing your encryption and security knowledge.  Thanks!

---

