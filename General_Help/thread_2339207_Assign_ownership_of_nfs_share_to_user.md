---
title: "Assign ownership of nfs share to user"
date: 2016-10-05
forum: General Help
---

### Post by jdo300 on 2016-10-05
Hello All,

I'm working on a bash configuration script for a set of servers that I am clustering together using MPI-CH. As part of the tutorial I'm following ([located here]("https://help.ubuntu.com/community/MpichCluster")), they want you to create a folder and set it as a mount point for an nfs share on another networked computer. Then, the goal is to create a new user and then assign that user's home directory to the mounted share folder. Here is the code for my script below:

```
masterIPAddress="10.10.2.1"
mGID=1003
mUID=1004

echo "Installing Files for MPI-CH..."

# Install NFS client to synchronize the common cluster files folder
echo 'y' | sudo apt-get install nfs-client

# Create and mount folder for shared cluster files
sudo mkdir /home/clusterFiles
sudo mount $masterIPAddress:/home/clusterFiles /home/clusterFiles

# Add entry in fstab file to automount folder on system start
echo "# Shared folder for MPI-CH" | sudo tee -a /etc/fstab
echo "$masterIPAddress:/home/clusterFiles    /home/clusterFiles    nfs" | sudo tee -a /etc/fstab

# Remount all partitions
sudo mount -a

# Create group for clustersim user
sudo addgroup clustersim --gid $mGID

# Create new user and assign clusterFiles folder as home directory
sudo adduser clustersim --disabled-login --gecos clustersim --uid $mUID --gid $mGID
echo "clustersim:password" | sudo chpasswd

# Add user to sudo group, move home folder to clusterFiles and set permissions
sudo usermod -aG sudo clustersim
sudo usermod --home /home/clusterFiles --move-home clustersim
sudo chown clustersim /home/clusterFiles
```

When I execute this script on a fresh install of Ubuntu 14.04, everything runs fine until the last line where it prints:

```
chown: changing ownership of ‘/home/clusterFiles’: Operation not permitted
```

I even tried manually following the instructions and adding the user through the GUI, but I get the same result. I *think* it may have something to do with the fact that the folder is a mount point, but I'm not sure what to do to fix it. So far, I tried adding the "user" flag to the fourth column in the fstab entry, thinking that maybe allowing users to mount the drive would fix it, but no joy so far. Any ideas?

Thanks,
Jason O

---

### Post by SeijiSensei on 2016-10-06
Does the clusterFiles user already exist on the NFS server?  Does the user on the client machine have the same UID and GID as the one on the server?  

You're also missing some fields from the /etc/fstab entry.  On my NFS clients, the entry looks like this:
```
192.168.1.100:/home  /path/to/mount/point   nfs     defaults,rsize=32768,wsize=32768,async,vers=3   0 0
```
I enforce version 3 because of some incompatibilities between my clients and server.  I use async writes because I'm not worried about loss of data on my server which is connected to a UPS.  I also bump up the read and write buffer sizes since the default value of 8192 bytes comes from the days of 10BaseT Ethernet.  I've used values as high as 65536 without incident.

---

### Post by jdo300 on 2016-10-09
> **SeijiSensei said:**
> Does the clusterFiles user already exist on the NFS server?  Does the user on the client machine have the same UID and GID as the one on the server?  

You're also missing some fields from the /etc/fstab entry.  On my NFS clients, the entry looks like this:
```
192.168.1.100:/home  /path/to/mount/point   nfs     defaults,rsize=32768,wsize=32768,async,vers=3   0 0
```
I enforce version 3 because of some incompatibilities between my clients and server.  I use async writes because I'm not worried about loss of data on my server which is connected to a UPS.  I also bump up the read and write buffer sizes since the default value of 8192 bytes comes from the days of 10BaseT Ethernet.  I've used values as high as 65536 without incident.

Hi SeijiSensei,

Sorry for the late reply, In my case, I have the same user with same UID and PID on both the NFS server and client machines. I did update my fstab entry to reflect your suggestion. I then rebooted the machine and tried changing the ownership, with the same result.

However, I later had the bright idea to simply check the permissions settings for the clusterSim folder and it looks like it was already set to the clusterSim user. Also, I was able to confirm that I can sync, and read and write files from and to the folder if I'm logged in as clusterSim or root. So it *seems* like it is working fine, despite the error I got initially.

I'm thinking that maybe the system doesn't let you change ownership of the folder if it is a network share owned by another machine? In my case, it seems to be OK but would like to understand this better for future reference.

Thanks,
Jason O

---

### Post by SeijiSensei on 2016-10-10
No, you can't change the top-level ownership of the share AFAIK.  You can create folders within the share with different ownerships if you are in the same group as the other user and have group-writable permissions.

---

### Post by jdo300 on 2016-10-11
Ahh thank you for the clarification. :D

---

