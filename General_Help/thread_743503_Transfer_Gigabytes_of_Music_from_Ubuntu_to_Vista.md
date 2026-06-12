---
title: "Transfer Gigabytes of Music from Ubuntu to Vista?"
date: 2008-04-02
forum: General Help
---

### Post by Mr.Zim on 2008-04-02
Hello all,

I currently use Windows Vista and I need to transfer about 2,769 songs from my Ubuntu PC to my Vista PC. The easiest way to do this would be to pop the hard drive containing the music into my Vista PC, but then I would have to stumble around trying to get Vista to read to EXT3 file system. The next easiest would be to connect both up to my network at a time and transfer from the Linux end. (Can I explore the entire hard drive from Linux?) The next easiest would be to upload it all to my web server then download it back down, which will take HOURS on end.

So, I have concluded that the network solution is best for me. If I understand correctly, I need to hit ALT+F2 and type "smb://172.0.0.1" where "172.0.0.1" is the IP of the Windows PC. Is this correct? Will I be able to transfer my music from the Linux side?

I have also heard of connecting them directly via a patch cable. Can anyone enlighten me on how this will work? Thank your much.

Steven

---

### Post by ryanhaigh on 2008-04-02
If you want to use a crossover cable you will need to assign ips statically and then yes smb://ip should work, you will need to have a share on the vista machine writable. Alternately you can setup a share on ubuntu and access it from vista (there are many howtos on setting up samba). Probably the easiest solution would be to install openssh-server on ubuntu and access the machine using winscp from ubuntu.

---

### Post by tubasoldier on 2008-04-02
Do you have a router or crossover cable?

I personally think the best way would be to use ssh.
install openssh on Linux. Install Putty in Windows to connect. (google putty).

Then transfer music.

---

### Post by LaRoza on 2008-04-02
You can read and write to Vista with Ubuntu 7.10.

If it is going to be a one time thing, you can just put the drive in and transfer it using Ubuntu.

It may be better to make a separate partition for this, so Ubuntu isn't reading or writing to important partitions. You can use NTFS and make and format the partition from Vista. (In Computer Management->Disk Management)

If you want to be transfering often, you can use the tools mentioned above (for a computer to computer connection, you need a cross over cable), or you can get yourself an external drive for shared data.

---

### Post by ryanhaigh on 2008-04-02
> **tubasoldier said:**
> Install Putty in Windows to connect. (google putty).
Then transfer music.

WinSCP will provide a nicer easier to use interface to the ssh server, whilst there is no doubt putty rocks for file transfers WinSCP is very simple and easy to understand.

---

### Post by kevdog on 2008-04-03
Ive had problems with smb hanging with large transfers.  It gets about 2Gb in then.....nothing, hangs.  Hopefully that is just me.  Its a wireless laptop to wired computer transfer using wireless.

---

