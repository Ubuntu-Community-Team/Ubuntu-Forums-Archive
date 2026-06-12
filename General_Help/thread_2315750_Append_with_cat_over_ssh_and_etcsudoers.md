---
title: "Append with cat over ssh and /etc/sudoers"
date: 2016-03-02
forum: General Help
---

### Post by Drenriza on 2016-03-02
Hi all

I would like to copy a series of mysql dumps through a bash script over ssh using cat from Machine#1 to remote#1

##Test to see if i can run the cat command on the remote machine.
```
echo "Date today is ${DATE}" |ssh -t -v user@xx.xx.xx.xx "sudo /bin/cat >> /mnt/destination/test.txt"
```

ssh debug1
> debug1: Sending command: sudo /bin/cat >> /mnt/destination/test.txt

On remote#1 in /etc/sudoers i have an entry for this
```
user ALL=(ALL:ALL) NOPASSWD: /bin/cat /mnt/destination/test.txt
```

Which results in
> bash: /mnt/destination/test.txt: Permission denied

The issue as i see it, is that the command i send isin't the same as the one in the sudoers file (as is). 
Which is because that /etc/sudoers dont allow the > character without failing being parsed by visudo -c even when escaping the character with \

Any help / suggestions is much appreciated!

Also will tee -a give the same result as cat >> ?

Thanks in advance
Kind regards!

---

### Post by HermanAB on 2016-03-02
I would use scp instead.

---

### Post by Drenriza on 2016-03-02
> **HermanAB said:**
> I would use scp instead.

You can copy standard stdrr directly to scp or you mean you would create a local file first and than scp the entire thing?

---

