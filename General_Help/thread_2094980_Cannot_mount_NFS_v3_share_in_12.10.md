---
title: "Cannot mount NFS v3 share in 12.10"
date: 2012-12-15
forum: General Help
---

### Post by supremedalek on 2012-12-15
I have a nfs server (unfortunately v3 but I am working on that), a centos 6.3, a osx 10.7, and a ubuntu 12.10 boxes. I was setting up these machines to access the nfs server. The centos box works fine and I have autofs working on it. I went so far on the osx box to nfs mount the share; still need to do the autofs bit. But, on the 12.10 desktop I seem to have a few issues. 

So, here are the steps I used (stolen from [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client):](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client):)

1. Install rpcbind nfs-common
2. try to mount
```
raub@desktop:~$ showmount -e fileserver
Export list for fileserver:
/volume1/home 10.0.0.0/24
raub@desktop:~$ sudo mount -t nfs  fileserver:/volume1/home /mnt                
mount.nfs: rpc.statd is not running but is required for remote locking.         
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.          
mount.nfs: an incorrect mount option was specified                              
raub@desktop:~$ 
```
3. Is statd running?
```
raub@desktop:~$ ps -ef|grep statd                                                               
statd     5737     1  0 20:51 ?        00:00:00 rpc.statd -L                    
statd     5748     1  0 20:52 ?        00:00:00 rpc.statd --no-notify           
raub      5753  3942  0 20:52 pts/0    00:00:00 grep --color=auto statd         
raub@desktop:~$ rpcinfo -p                                                      
   program vers proto   port  service                                           
    100000    4   tcp    111  portmapper                                        
    100000    3   tcp    111  portmapper                                        
    100000    2   tcp    111  portmapper                                        
    100000    4   udp    111  portmapper                                        
    100000    3   udp    111  portmapper                                        
    100000    2   udp    111  portmapper                                        
    100024    1   udp  57904  status                                            
    100024    1   tcp  58595  status                                            
raub@desktop:~$
```

What else should I be looking at?

---

### Post by Rexilion on 2012-12-15
Just for troubleshooting: Could you try with the '-o nolock' mount parameter?

---

### Post by supremedalek on 2012-12-15
Oh, sorry for that. Yeah, with the '-o nolock' it works. Why it does not want to use the rpc.statd that is running?

---

### Post by Rexilion on 2012-12-15
Please post the output of:

```
sudo cat /etc/hosts.deny /etc/hosts.allow
```

---

### Post by supremedalek on 2012-12-15
For /etc/hosts.deny,
rpcbind : ALL

For /etc/hosts.allow,
rpcbind : 10.0.0.18

where 10.0.0.18 is the fileserver's IP. So I commented them out and then tried again. It worked this time, which confuses me.

---

### Post by Rexilion on 2012-12-15
I guess that rpcbind is required to make things work properly. And I can conclude from that (guess! I'm not an expert) is that the OSX and Centos versions are not using locking =). Hence they do not complain of lack thereof.

Is that an option?

---

### Post by supremedalek on 2012-12-19
I am really not sure. I thought my /etc/hosts.allow rule (only get rpcbind from the fileserver) made sense. Something is missing here and I do not know what...

---

### Post by Rexilion on 2012-12-20
Try throwing things wide open and test your situation again. Will the other hosts use locking? If yes, then you misconfigured your security with respect to locking.

Also, locking is a relatively new feature that was added later to NFS (in this form). So older clients might not support it at all. Check your versions for that one.

---

### Post by rnerwein on 2012-12-20
> **Rexilion said:**
> Try throwing things wide open and test your situation again. Will the other hosts use locking? If yes, then you misconfigured your security with respect to locking.

Also, locking is a relatively new feature that was added later to NFS (in this form). So older clients might not support it at all. Check your versions for that one.
hi
hope you have fixed your problem already - when not here is my entry from 
/etc/hosts.allow
rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1 127.0.1.1 193.149.32.2

im running ubuntu 12.04 LTS, sun solaris 10 and suse 11 - no problems
may be it will help you
cheers

---

### Post by Chao-Lin_Cho on 2013-10-09
> **rnerwein said:**
> hi
hope you have fixed your problem already - when not here is my entry from 
/etc/hosts.allow
rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1 127.0.1.1 193.149.32.2

im running ubuntu 12.04 LTS, sun solaris 10 and suse 11 - no problems
may be it will help you
cheers

After I added the above suggestion to my /etc/hosts.allow everything worked like a charm. Thank you.

---

### Post by m4z on 2013-12-01
this tread helpme to solve the same problem, thanks..

---

### Post by ape1972 on 2014-01-02
Hello together!

after a long search for fixing the mentioned problem I had with my Raspberry Pi being a NFS client, the tip of rnerwein was dismanteling the issue:
the loopback ip was missing. Adding both 127... solved the problem.
Just for understanding: Has somebody a glue what went wrong without?

Again many thanks to rnerwein!

Regards,
Andreas

---

