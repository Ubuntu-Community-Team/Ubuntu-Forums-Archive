---
title: "Unabel to Mount Network Drive"
date: 2020-09-26
forum: General Help
---

### Post by greatoffender on 2020-09-26
I did have a similar thread a few weeks back but find myself in the same situation again.

Raspberry pi set up as an NAS server. I don't think it is specific to raspberry pi and feel it may be a more general Linux question so I'll try again.. The model is a Pi 3 B+ that I never found a use for so I took a couple of old USB drives and hooked them up using a guide  from PiMyLifeup (samba). I tinkered with the first installation so many times and couldn't get to work with my Ubuntu Cinnamon laptop that I just reinstalled and it worked. But only for a short period of time and now find myself denied. All Windows machines have no issue accessing. 

I am trying to log in as "pi" with the correct username/password combo. My samba.conf info is below. I did try and add a line at one time to force=pi but had no luck. Any ideas? Wish I was more of a Linux veteran but after 20+ years I have made the permanent switch and I'm not going back. 

Thanks for looking!

[HomeServer]
path = /media/pi/SimpleDrive
writeable=Yes
create mask=0777
directory mask=0777
public=no

---

### Post by TheFu on 2020-09-27
That isn't a valid smb.conf file.  Run testparm and post the output, please.
Look through the log files. These are probably in /var/log/ and /var/log/samba/

If "All Windows machines have no issue accessing.", what's the problem? I'm confused.

---

### Post by greatoffender on 2020-09-27
The issue is the irony of the only Linux machine on the network not being able to connect. I recently have given up on Windows. Don't know why I could mount the drives on the laptop on a Monday and not be able to mount them on Tuesday? I am not going back to Windows so any assistance you can provide would be of great value! What's wrong with the smb.conf file?

testparm is quite lengthy but I don't see any obvious issues. Is there any particular section you are interested in?

[HomeServer]
    create mask = 0777
    directory mask = 0777
    path = /media/pi/SimpleDrive
    read only = No

Log file from the laptop is repetitive with the same entries based on the time and date of the attempts but are as follows:
change_to_user_internal: chdir_current_service() failed!
[2020/09/27 13:01:30.477064,  0] ../source3/smbd/uid.c:453(change_to_user_internal)

---

### Post by TheFu on 2020-09-27
If you don't have Windows, then use NFS.

If you want samba, the entire smb.conf file is needed. The different settings interact. You can't pick and choose when it comes to troubleshooting. Plus, I'm hardly a samba expert.  I'm much better with NFS.

And the file systems for the shared directories would be helpful too.  Using NTFS on a shared disk is an issue that needs other settings from the mount options.

---

### Post by greatoffender on 2020-09-27
Good to know. I have been playing with Linux since the late 90's but always found it a hassle for numerous reasons but this go around seems much more stable. I'm old enough to admit I was using DOS when it was new and then progressed through every version of Windows because that was always the business standard at work.

I am going to try NFS and may come back to lean on you. Quick question, will samba and NFS work together? I'm sure I can Google this but ? never hurts to ask. Going to leave the thread open just in case.

Thanks for your help!

---

### Post by SeijiSensei on 2020-09-28
Yes, I share the same home directories on my server using both Samba and NFS.

Did you create a Samba user using 
```
sudo smbpasswd -a pi
```
Samba does not use /etc/passwd for authentication. It has its own schemes.

---

### Post by TheFu on 2020-09-28
> **greatoffender said:**
> Good to know. I have been playing with Linux since the late 90's but always found it a hassle for numerous reasons but this go around seems much more stable. I'm old enough to admit I was using DOS when it was new and then progressed through every version of Windows because that was always the business standard at work.

I am going to try NFS and may come back to lean on you. Quick question, will samba and NFS work together? I'm sure I can Google this but ? never hurts to ask. Going to leave the thread open just in case.

Thanks for your help!

I was lucky.  DOS and Windows were not the standards everywhere I worked.
Samba and NFS do not work together, but they can be run on the same systems for clients and servers, if necessary. They are separate systems, using separate protocols, with very different goals.

CIFS is user -to- system. End users are involved in the connections. CIFS is controlled by Microsoft and beholding to whatever issues their implementation may uncover, cause, or inflict.

NFS is system -to- system. Administrators setup connections and end users see the NFS storage just like local storage, with the same native permissions.  NFS has been stable for 30 yrs with only 3 versions in that time.  v4 of NFS is automatically backwards compatible with v3. If you want to use the added security that NFSv4 can provide or added performance that v4.1 can provide, then you can do that as the administrator. End users don't know anything about these changes.  The v4 security adds encryption that is secure enough to use over the internet without any VPN.  The performance improvements can be used to access clustered storage from multiple sources concurrently, so instead of being limited to the throughput for a single NFS server and disks, the number of NFS nodes in the cluster and copies of data spread across all those nodes can be brought into the total throughput available.  Again, end-users don't need to know anything about these aspects.  Effectively, if you have a 5 node NFS cluster with 8 disks each and 40 copies of the data to be retrieved, then the performance isn't limited to what 1 server can provide, but to what 5 servers with 8 HDDs - 40x what a single copy can provide. This assumes any network bandwidth limits are also addressed.  And all of this is $0.  No add-on license necessary.  Today, NFSv4.1 isn't widely used, but v4 has been available for about 15 yrs. It is extremely stable and fast.

---

### Post by greatoffender on 2020-10-05
So I tried the NFS setup with mixed results. First, there are no two guides on the entire web that tackle this the same way which I found to be infuriating. And when I did finally mount the Pi I couldn't access the drives because? That led me down a rabbit hole until I figured out how to mount the drives bur by that time I was exhausted. There's nothing wrong with an education and I always enjoy learning something new but ... I went back to Pi and started over from scratch since there was nothing on it anyway. Long story short, I found an article about someone having issues with Mint 19 and Samba ([https://bdmpublications.com/linux-mint-19-1-samba-fix/](https://bdmpublications.com/linux-mint-19-1-samba-fix/)) and this seemed to have straightened it out but who knows since I've had it working before. Samba was just so easy and straightforward but also gives the family an easy in if they need it. Nothing important on the drive except a half a lifetime of music and a few years worth of videos.

I do appreciate all of the help and I envy your knowledge and experience. My younger days of being a network guru are long behind me as I now occupy my life as an analyst staring mindlessly at spreadsheets all day. Doesn't mean I've given up because for my final act I decided to adopt Linux full time in my home life. Much to learn and plenty of time to do it.

Thank you again!

---

### Post by greatoffender on 2020-10-05
> **SeijiSensei said:**
> Yes, I share the same home directories on my server using both Samba and NFS.

Did you create a Samba user using 
```
sudo smbpasswd -a pi
```
Samba does not use /etc/passwd for authentication. It has its own schemes.

That was the easy part. There have to be 10 different guides on doing this and fortunately they are all the same but it doesn't mean I don't appreciate the support. I have found my answer after a few weeks of searching (posted above) so now the real test is how long it will last as I've gotten this far before.

Thank you!

---

### Post by TheFu on 2020-10-05
> **greatoffender said:**
>  Nothing important on the drive except a half a lifetime of music and a few years worth of videos. 

I really hope you have backups for that data!

BTW, I've never been a network engineer. That's a very different class of skills than I hold. I know enough, but would never make it in a network engineering role at any company.

When you decide to learn Linux, some guided learning, in order, is the most efficient: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle book.  

As for NFS, the guides cannot assuming anything about your setup, so they have to handle every foolish thing that people try. Most of the time, 
[LIST]
[*]On the server, 
[LIST]
[*]there's 1 install command (nfs-server) and 
[*]1 line added to /etc/exports
[/LIST]
[*]On the client, 
[LIST]
[*]there's 1 install command and 
[*]1 line added to /etc/fstab
[/LIST]
[/LIST]

That's it.  The a **mount -a** from the client and Bob's your uncle.

Now, there are a bunch of assumptions around those simple steps, which uninformed, former, Windows people usually don't also have setup.  Understand of Unix file and directory permissions, DNS, centralized usernames and groups managed are the biggies.  That's why the instructions are often longer than necessary.  
Samba ignores Unix file and directory permissions and instead uses a separate user DB, which is also a huge problem for people setting up samba. If you forget that and aren't using centralized MS-Active Directory, samba won't work either. 

Everything has pros and cons.  For me, native Unix permissions is a huge PRO, but for people who don't understand those, it can be a huge CON.  Used to be that NFS was much faster than Samba. These days, it is a coin toss for which is faster, but for streaming media, NFS **does** perform in a better way to prevent stuttering that happens when Samba is used.

Anyways, if you are happy, then we're happy.  Sometimes samba is the best tool for the job.

---

