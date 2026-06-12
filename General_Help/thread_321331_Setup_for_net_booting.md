---
title: "Setup for net booting"
date: 2006-12-18
forum: General Help
---

### Post by tari on 2006-12-18
I'm trying to set up a machine as an extremely lightweight frontend to my MythTV backend system, and if possible, I'd love to make it diskless.  Problem is, I don't know how I would go about setting up the system, and setting up my local server to have this frontend network boot from an NFS share.  So, my questions:
1: Would it be possible to install Ubuntu to an NFS share, and if so, how?
2: How to configure my server to allow network booting of clients?

---

### Post by hot_rod_hippie on 2008-02-29
I had a setup just to run a diskless node from an Ubuntu server running 6.10.  After much looking around, I got it all configured.  From my notes, this is how I did it (I think...I don't remember some of my shorthand, and I no longer use the system after I replaced the server). I apologize if it is similar to anyone's post on any forum, as my notes copied lots of code from others.

Hopefully it works for you. If anyone wants to make corrections or knows a better way, please feel free.

BIOS must support boot from LAN

You will need the NFS packages, a DHCP server, a TFTP server, and a file from the PXELinux tarball ([http://syslinux.zytor.com/pxe.php](http://syslinux.zytor.com/pxe.php)), along with the associated packages.
	*sudo apt-get install nfs-common nfs-kernel-server dhcp atftp xinetd*

Partition drives so that there is a separate partition for each node/frontend you want.  Format with ext3.

Insert an install CD and choose one of the extra partitions as / for the new install...take steps as necessary, but DO NOT install a boot loader (hardware config is much easier if you have the same/similar in the server and client, it just takes some tweaking otherwise).  This will need to be done for each frontend (or copy from one partition to the others).

Create an entry in /etc/fstab so the server will mount the partition on boot:
	*/dev/hda2(or device name)	/desired/mount/point	ext3	defaults	0	2*

NFS
Next you need to modify /etc/exports to assign root partitions to each frontend:
	[I]/desired/mount/point	192.168.1.0/24(rw,no_root_squash,sync,no_subtree_check)
	/home			192.168.1.0/24(rw,no_root_squash,sync,no_subtree_check)[/I]

Restart NFS (on the server):
	*sudo /etc/init.d/nfs restart*

DHCP
Edit /etc/dhcpd.conf to assign a static address to the client MAC (the following is important)
	[I]subnet 192.168.1.0 netmask 255.255.255.0 {
		range 192.168.1.100 192.168.1.200;
		option broadcast-address 192.168.1.255;
		option routers 192.168.1.1;
	}
	
	clientbox1 {
		hardware ethernet 00:11:22:33:aa:bb;
		fixed address 192.168.1.10;
		option root-path &#8220;desired/mount/point&#8221;;
	}
[/I]
TFTP
To make xinetd start atftpd, create a file atftpd in /etc/xinetd.d that contains the following:
	[I]service tftp
	{
		disable		= no
		socket_type	= dgram
		protocol	= udp
		wait		= yes
		user		= nobody
		server		= /usr/sbin/in.tftpd
		server_args	= --tftpd-timeout 300 --retry-timeout 5 
			--mcast-port 1758 --mcast-addr 239.239.239.0-255
			--mcast-ttl 1 --maxthread 100 &#8211;verbose=5	/tftpboot
	}[/I]

Now that you have referenced /tftpboot, you need to make the directory:
	[I]sudo mkdir /tftpboot
[/I]
Give everyone rights:
	*sudo chmod 777 /tftpboot*

PXE
Get the pxelinux.0 file from the tarball and put it in /tftpboot

Configure the initial ramdisk to load in the node:
	[I]sudo chroot /desired/mount/point /bin/bash
[/I]
Edit /etc/initramfs-tools/initramfs.conf and change:
	*BOOT=local*
to
	*BOOT=nfs*

Reload the updated ramdisk
	*sudo update-initramfs -u*
Take note of the output path and file name

Close chroot:
	*exit*

Copy the new ramdisk to /tftpboot
	[I]sudo cp /desired/mount/point/boot/initramfs.img-[kernel-version] /tftpboot
	sudo cp /desired/mount/point/boot/vmlinuz-[kernel-version] /tftpboot[/I]
-where [kernel-version] is the output of uname -r

Make a directory for PXE:
	*mkdir /tftpboot/pxelinux.cfg*

Make PXE config file named 01-00-11-22-33-aa-bb (replace 00-11-22-33-aa-bb with the MAC address of the frontend).  It should contain the following, where 192.168.1.1 is replaced with the server's ip:
	[I]default linux

	label linux
	kernel vmlinuz-[kernel-version]
	append initrd=initrd.img-[kernel-version] \\
		nfsroot=192.168.1.1:/desired/mount/point[/I]

Make a similar file for each additional frontend.

Set the diskless frontend to boot from LAN (or other config your motherboard may require for PXE booting).

Add the server's /home directory to /etc/fstab once the frontend boots:
	*192.168.1.1:/home	/home		nfs	defaults	0	0*
-This makes the frontend's /home the same as the server's /home

Reboot the node and everything should work.

---

