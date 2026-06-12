---
title: "Server file copy slow when executing from client"
date: 2014-11-21
forum: General Help
---

### Post by Gordon D on 2014-11-21
Hi,

I am running an UBUNTU Server 14.04 with multiple 14.04 clients. I have two separate physical SATA drives on my server. When I SSH to the server and do a copy (cp) of a large file between the drives it is almost instantaneous, but when I do the same from any of the clients is takes a very long time. It almost seems like the copy is being done across the network, so the transfer is being throttled by my LAN speed.

Any assistance would be much appreciated.

Cheers

Gordon

---

### Post by bashiergui on 2014-11-22
Where is the server in relation to these clients? Are they all on the same host or are they independent machines on a LAN?

---

### Post by sandyd on 2014-11-22
> **Gordon D said:**
> Hi,

I am running an UBUNTU Server 14.04 with multiple 14.04 clients. I have two separate physical SATA drives on my server. When I SSH to the server and do a copy (cp) of a large file between the drives it is almost instantaneous, but when I do the same from any of the clients is takes a very long time. It almost seems like the copy is being done across the network, so the transfer is being throttled by my LAN speed.

Any assistance would be much appreciated.

Cheers

Gordon

How are the files being accessed from the client?

Some transfer methods will cause the file to be copied onto the client, then back on the server as the new file.

---

### Post by Gordon D on 2014-11-22
Just using Terminal cp, or copy/paste in the Files GUI app.

---

### Post by Gordon D on 2014-11-22
Fairly simple server setup on a single LAN:-

Server --<wired>-- 8 port Gigabit Switch --<wired>-- Wireless Router --<wired>-- ADSL Modem

The majority of the clients connect through the wireless router, but there are few that are cabled directly to the Gigabit switch. When I do a copy from one of the wired clients I get about 44MB/sec transfer rate, but doing it in the wireless clients I only get about 1.1MB/sec. Both results are a lot slower than I would expect from a server disk to server disk copy on a single physical server.

---

### Post by sandyd on 2014-11-23
> **Gordon D said:**
> Fairly simple server setup on a single LAN:-

Server --<wired>-- 8 port Gigabit Switch --<wired>-- Wireless Router --<wired>-- ADSL Modem

The majority of the clients connect through the wireless router, but there are few that are cabled directly to the Gigabit switch. When I do a copy from one of the wired clients I get about 44MB/sec transfer rate, but doing it in the wireless clients I only get about 1.1MB/sec. Both results are a lot slower than I would expect from a server disk to server disk copy on a single physical server.

I meant how are the clients accessing the files remotely - via samba? NFS?

See [http://wiki.samba.org/index.php/Server-Side_Copy](http://wiki.samba.org/index.php/Server-Side_Copy) for samba and why its slow and not doing the copying server side on 'nix clients.

---

### Post by SeijiSensei on 2014-11-23
The copying is almost certainly happening via the client.  So you have large amounts of data flowing from the server to the client and back again.  If you're doing this over wifi, you're doubly encumbered since wifi is a "[half-duplex]("http://www.makeuseof.com/tag/what-is-half-duplex-and-full-duplex-operation-and-how-does-it-affect-your-router/")" protocol.  Full-duplex connections like Ethernet use one dedicated pair of wires for upstream transmissions and a second pair for downstream reception.  Wifi has to "turn the line around" and cannot maintain simultaneous data streams.

---

### Post by Gordon D on 2014-11-23
> **SeijiSensei said:**
> The copying is almost certainly happening via the client.  So you have large amounts of data flowing from the server to the client and back again.  If you're doing this over wifi, you're doubly encumbered since wifi is a "[half-duplex]("http://www.makeuseof.com/tag/what-is-half-duplex-and-full-duplex-operation-and-how-does-it-affect-your-router/")" protocol.  Full-duplex connections like Ethernet use one dedicated pair of wires for upstream transmissions and a second pair for downstream reception.  Wifi has to "turn the line around" and cannot maintain simultaneous data streams.

Yes, this seems to be very much the symptoms, although I was hoping it would be smart enough to realise it was really only a local copy on the server.

---

### Post by Gordon D on 2014-11-23
> **sandyd said:**
> I meant how are the clients accessing the files remotely - via samba? NFS?

See [http://wiki.samba.org/index.php/Server-Side_Copy](http://wiki.samba.org/index.php/Server-Side_Copy) for samba and why its slow and not doing the copying server side on 'nix clients.

Oh. Sorry. Using NFSv4, although the Samba issue seems to be very much what is happening.

FSTAB entries - 
# Server
192.168.x.x:/srv		/nfs/srv	nfs4 _netdev,auto 	0	0
192.168.x.x:/srv2tb		/nfs/srv2tb	nfs4 _netdev,auto	0	0

---

### Post by sandyd on 2014-11-24
> **Gordon D said:**
> Oh. Sorry. Using NFSv4, although the Samba issue seems to be very much what is happening.

If you like being hacky, NFS *can* do server side copying, though I don't know why you would want to go through all of that.
[http://wiki.linux-nfs.org/wiki/index.php/Server_Side_Copy](http://wiki.linux-nfs.org/wiki/index.php/Server_Side_Copy)

---

### Post by Gordon D on 2014-11-24
Ah, so NFS doesn't support native server side copy by the looks of it, without resorting to some hacking. There is some reference to it being a proposed extension to NFSv4.2, but I assume this hasn't happened yet. Samba looks like it may do it, but I am loathed to switch to it.

---

### Post by redmk2 on 2014-11-24
> **Gordon D said:**
> Oh. Sorry. Using NFSv4, although the Samba issue seems to be very much what is happening.

FSTAB entries - 
# Server
192.168.x.x:/srv		/nfs/srv	nfs4 _netdev,auto 	0	0
192.168.x.x:/srv2tb		/nfs/srv2tb	nfs4 _netdev,auto	0	0

This sure sounds like you need to use the *async* parameter in the /etc/exports files.  The default is to use: *sync* which constantly sync's the files to the disk and flushes the buffers.  This really slows down copying data.  From the man pages for exports ```

man exports
...
       async  This option allows the NFS server to violate the NFS protocol and reply to requests
              before any changes made by that request have been committed to stable storage (e.g.
              disc drive).

              Using this option usually improves performance, but at the  cost  that  an  unclean
              server restart (i.e. a crash) can cause data to be lost or corrupted.

       sync   Reply to requests only after the changes have been committed to stable storage (see
              async above).

              In releases of nfs-utils up to and  including  1.0.0,  the  async  option  was  the
              default.   In  all  releases  after  1.0.0,  sync is the default, and async must be
              explicitly requested if needed.  To help make system administrators aware  of  this
              change, exportfs will issue a warning if neither sync nor async is specified.



```

---

### Post by Gordon D on 2014-11-24
> **redmk2 said:**
> This sure sounds like you need to use the *async* parameter in the /etc/exports files.  The default is to use: *sync* which constantly sync's the files to the disk and flushes the buffers.  This really slows down copying data.  From the man pages for exports ```

man exports
...
       async  This option allows the NFS server to violate the NFS protocol and reply to requests
              before any changes made by that request have been committed to stable storage (e.g.
              disc drive).

              Using this option usually improves performance, but at the  cost  that  an  unclean
              server restart (i.e. a crash) can cause data to be lost or corrupted.

       sync   Reply to requests only after the changes have been committed to stable storage (see
              async above).

              In releases of nfs-utils up to and  including  1.0.0,  the  async  option  was  the
              default.   In  all  releases  after  1.0.0,  sync is the default, and async must be
              explicitly requested if needed.  To help make system administrators aware  of  this
              change, exportfs will issue a warning if neither sync nor async is specified.



```

Already using async. Exports file :-

/nfs/srv             192.168.x.0/24(rw,nohide,insecure,no_subtree_check,no_root_squash,async)
/nfs/srv2tb        192.168.x.0/24(rw,nohide,insecure,no_subtree_check,no_root_squash,async)

---

