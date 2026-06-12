---
title: "Samba Bug Workaround?"
date: 2021-01-14
forum: General Help
---

### Post by ryanmills on 2021-01-14
I seem to be having a lot of drama with this bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476)

I first noticed this bug when I upgraded a file server from 18.04 to 20.04 last month. During that time I installed new drives. The old drives shared fine, the new drive share is broken. Viewing from both Windows 10 machines and other a 20.04 machine shows files as folders, zero sized files, ect. Even more interesting if I copy those same files to a working share, it breaks there as well, but only those files. What really cook my noodle, take this example, share1 works, I copy a few files from share1 (where they work fine) to share2 on the server (not over SMB) and they fail when viewed over SMB (files and folders, zero size files). If copy the files from share2 to a new location on share1 they now fail on share1 even though all other files on share1 work, in fact the original files on share1 that I copied, work but not once they have been copied to the share that sometimes does not work. basically some shares work, others don't but even then some files work and some files don't in this case these were newer files but I did not look that hard, I have a real fear I will wipe out files by mistake.

To mitigate the issue I setup a second server with a clean 20.04 install. It's shares worked fine but needed more space, added another driver and boom, same bug. I know its not an SMB1 issue for me, I disabled it on the windows 10 machine and insured 2:4.11.6+dfsg-0ubuntu1.6 was installed and made sure SMB3 was is in use with smbstatus for both Ubuntu clients and Windows 10 clients. It seems confirmed in the notes that its a SMB3 issue as well however there has not been any movement I can see on the bug for several months now. It also works just fine on some drives but I can't figure out what specifically makes it work with some shares and not others. First thought was formatting/portioning. But I have working shares on exactly the same settings. Given this bug has effected 20.04 since it's launch and there are no pitchforks out I'm assuming there must be some workaround or some way to share that avoid the GIO issue. Or perhaps something I'm doing wrong when creating shares. Since 18.04 I have just used the built in create local share and let it set permissions. 

Been struggling with this for a month now, several times I have spent hours googling but I just can't make it work over SMB3, any advice is welcome.

---

### Post by rsteinmetz70112 on 2021-01-14
Have you tried setting the MAX protocol in Samba and not using SMB3?

---

### Post by ryanmills on 2021-01-15
> **rsteinmetz70112 said:**
> Have you tried setting the MAX protocol in Samba and not using SMB3?

Bug exists in SMB2 and I could not get windows 10 to connect to the shares if I forced NT1 despite that SMB1 is enabled in windows 10 and can connect to older SMB1 network shares on NAS's. Burned 3 hours trying. The ubuntu release is almost a year behind the samba current release and I don't see anything in the notes about it being fixed in the latest. I assume this has to be a ubuntu issue since it was fine in 19.04 so I am out of ideas. It would be nice if just once, I could upgrade ubuntu and have everything work... If anyone knows how to get the latest samba version installed for 20.04 I would be welcome to try it. Not sure what else I can do other than switch to another OS.

---

### Post by HermanAB on 2021-01-15
Not what you want to hear but note that Windows supports the FTP protocol natively and there is also a NFS module available for download on technet.  So if you have a home network with one or two computers, then an anonymous FTP server, or a NFS server, would be much less hassle than a Samba server.

---

### Post by ryanmills on 2021-01-16
> **HermanAB said:**
> Not what you want to hear but note that Windows supports the FTP protocol natively and there is also a NFS module available for download on technet.  So if you have a home network with one or two computers, then an anonymous FTP server, or a NFS server, would be much less hassle than a Samba server.

Not really an option for me, looks like maybe its time to try centOS. Seems silly to learn a new distro over samba but I'm not sure what else to try.

---

