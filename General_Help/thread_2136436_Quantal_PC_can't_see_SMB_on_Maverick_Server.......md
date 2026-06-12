---
title: "Quantal PC can't see SMB on Maverick Server......"
date: 2013-04-17
forum: General Help
---

### Post by hogfan on 2013-04-17
I have a strange issue with SMB.  I have an Ubuntu server that is about 2 years old that I use as my media server and it is running Maverick.  No changes have been made on the server.  I recently had to re-install XBMCbuntu on the Acer Revo PC connected to my PC.  This machine still has the same host name it previously had "xbmc".  However, after re-installing the XBMCbuntu on the Revo (XBMCbuntu based on Quantal), I am unable to see my SMB shares on the the Maverick server.  SMB is however working as I can access SMB shares on other machines on the network.  The strange thing is when browsing SMB shares from the XBMCbuntu machine, I don't even see the Maverick server listed.  However, I am accessing the shares on the Maverick server via SMB from my Notebook running Linux Mint 13, and two Windows 7 machines.  Any ideas why the XBMCbuntu machine wouldn't be able to see the SMB shares on the server running Maverick?  I am using NFS as a workaround for now (and may stay with it anyway), but would like to know why this machine can't see the SMB shares on the server when other machines on the network can.  

Also, I have tried manually accessing the share via  smb://Mediaserver/mysharehere rather than browsing the workgroup, but the connection still times out.  Any insight into this is extremely appreciated.

-hogfan

---

