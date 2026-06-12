---
title: "libmtp error:  Could not get file from device. Android to Ubuntu 17.10"
date: 2018-02-21
forum: General Help
---

### Post by 7-webmaster on 2018-02-21
According to apt I have the latest version of libmtp on my Ubuntu 17.10 system

When my tablet is plugged in and mounted:

mtp-detect
libmtp version: 1.1.13

Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 1, dev 12
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
ignoring libusb_claim_interface() = -6LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.

If I try to unmount the device I get that one or more applications are keeping the interface busy.  If I tell it to unmount anyway I get backend is currently unmounting.

How do I copy files from my Android tablet to Linux?

Following advice from other threads I tried installing sshdroid on my tablet and connecting to the server from FileZilla:

Status:    Connecting to 192.168.1.3:2222...
Status:    Connection established, waiting for welcome message...
Response:    SSH-2.0-dropbear_0.53.1
Error:    Cannot establish FTP connection to an SFTP server. Please select proper protocol.
Error:    Critical error: Could not connect to server

Also the protocol requires a password.  What is the password?  My tablet is only protected by a pin.

I have now tried to reverse the direction and run an FTP  client on the Android tablet to access the FTP server on the Linux machine.  I entered the same options into the Android FTP client that I use on my laptop on the same network but the request fails when I use the name of the server.  I only succeed if I identify the server by its IP address rather than its name on the local network and use plain FTP.

---

