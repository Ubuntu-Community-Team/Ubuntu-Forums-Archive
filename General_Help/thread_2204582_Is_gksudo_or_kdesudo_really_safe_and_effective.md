---
title: "Is gksudo or kdesudo really safe and effective?"
date: 2014-02-09
forum: General Help
---

### Post by dave2001 on 2014-02-09
When using the command "kdesudo" in the kde4 desktop on ubuntu 13.10, the terminal spits out a long string of information, some of which looks like error messages to my untrained eyes (and I also remember this happening in previous versions, and with the gnome equivalent gksudo). Does this mean that there is a specific problem that I could fix? At the very least this seems there's a lot of "extra" stuff going on, that could possibly be minimized? Am I asking for trouble down the line by using the kdesudo/gksudo  command? Is there a more "robust" way of opening graphical applications with root privileges? 

Thanks in advance for any input!

I'll include an example of when I issued the command "kdesudo kwrite somefile"  
```
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(2653) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(2653) KBuildSycoca::checkDirTimestamps: timestamp changed: "/usr/share/mime/"
kbuildsycoca4(2653) kdemain: Reusing existing ksycoca
kbuildsycoca4(2653) KBuildSycoca::recreate: Recreating ksycoca file ("/var/tmp/kdecache-root/ksycoca4", version 228)
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/mixed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/digest.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/encrypted.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/related.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/report.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/x-mixed-replace.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/appledouble.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/alternative.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "multipart/signed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.WANDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.postgresql.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.libvirt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.svn.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.home-sharing.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.rdp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.adobe-vc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.telnet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.smb.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.pulse-sink.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ssh.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.WANConnectionDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.rfb.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.unknown.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.LANDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.device.unknown.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.PrinterBasic1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.Scanner1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.raop.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.lobby.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.MediaServer3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.eppc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ipp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.plasma.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.net-assistant.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.sip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.maemo-inf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.DigitalSecurityCamera1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.daap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.device.server.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.giver.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.PrinterEnhanced1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.rsync.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.lskat.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.dacp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.airport.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.BasicDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.MediaRenderer1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.touch-able.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.kbattleship.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.WFADevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ntp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.http.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/blockdevice.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/symlink.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.imap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/socket.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.h323.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.couchdb_location.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/chardevice.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.pdl-datastream.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.RADiscoveryAgent1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.odisk.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.MediaRenderer2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.webdav.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.device.scanner.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.skype.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.udisks-ssh.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.RemoteUIServerDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ftps.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.printer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.LightingControls1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.sleep-proxy.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.pulse-server.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.nfs.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.RAServer1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.WLANAccessPointDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.realplayfavs.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.appletv-itunes.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ldap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.RemoteUIClientDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ftp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.pop3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.xmpp-server.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.presence.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.Unknown.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/directory.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.workstation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.afpovertcp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.RAClient1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.device.router.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.SolarProtectionBlind1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.device.printer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.airmouse.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/mount-point.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.acrobat-server.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.appletv-pair.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.device.workstation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.sftp-ssh.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.kfourinline.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.pulse-source.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.webdavs.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.MediaServer2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ksirk.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.network.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.ggz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.InternetGatewayDevice1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/fifo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.nssocketport.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.HVAC1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "inode/vnd.kde.service.upnp.MediaServer1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-xcursor.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-portable-bitmap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-xfig.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-ilbm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-xbitmap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-xwindowdump.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/fax-g3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-fpx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-apple-ios-png.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-panasonic-raw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.ms-modi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-gzeps.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/fits.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-fuji-raf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/ief.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-eps.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-pentax-pef.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/gif.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-portable-anymap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/g3fax.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-dds.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-win-bitmap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.djvu.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-skencil.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-adobe-dng.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-wmf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-pic.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-macpaint.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-jng.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-sony-arw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-portable-graymap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.dxf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-quicktime.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-sony-sr2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-sgi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-sun-raster.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-kodak-k25.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-pcx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-sony-srf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.wap.wbmp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-minolta-mrw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-niff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-tga.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/openraster.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/bmp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/rle.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/svg+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-pict.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-bzeps.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/tiff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/dpx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/png.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-lws.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-kodak-dcr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-cmu-raster.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-compressed-xcf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-canon-crw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-kodak-kdc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.rn-realpix.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-applix-graphics.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-photo-cd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-msod.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-lwo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.dwg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-nikon-nef.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-dcraw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-dib.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.microsoft.icon.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-panasonic-raw2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-olympus-orf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-exr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-rgb.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/svg+xml-compressed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-canon-cr2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-sigma-x3f.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/vnd.adobe.photoshop.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-kde-raw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-hdr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-icns.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-portable-pixmap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-emf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/jp2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-xpixmap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-xcf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/x-3ds.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/jpeg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "image/cgm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-nsv.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-matroska.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-anim.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/mp2t.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/quicktime.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/mpeg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/vnd.rn-realvideo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/vnd.mpegurl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-sgi-movie.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-ms-wmv.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/isivideo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-flic.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/3gpp2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/dv.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-msvideo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/vivo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-theora+ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-mng.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/annodex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/mp4.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-javafx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/wavelet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-ms-wmp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-ms-asf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/webm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-flv.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/x-ogm+ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/3gpp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "video/ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/disposition-notification.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/x-gnu-rmail.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/external-body.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/delivery-status.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/rfc822.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/news.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "message/partial.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "uri/mmsu.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "uri/mms.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "uri/rtspt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "uri/mmst.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "uri/pnm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "uri/rtspu.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "packages/apport.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/audio-player.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/unix-software.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/blank-hddvd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/blank-bd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/blank-cd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/video-bluray.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/image-dcf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/image-picturecd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/video-hddvd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/video-dvd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/win32-software.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/audio-dvd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/ebook-reader.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/audio-cdda.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/blank-dvd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/software.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/video-vcd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-content/video-svcd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "all/all.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "all/allfiles.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ms-wim.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kommander.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-object.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pem-file.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xml-external-parsed-entity.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-abiword.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-graphite.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-type1.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs7-mime+pem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java-keystore.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bcpio.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pgp-keys.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-cab-compressed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/metalink4+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-plasma.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-applix-spreadsheet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kexiproject-shortcut.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-pcf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.template.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-dia-diagram.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-par2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/oda.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sv4crc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gtktalog.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-shar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-designer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-bdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.slide.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kontour.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-nautilus-link.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/javascript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-x509-ca-cert.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/rdf+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kpresenter.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ruby.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-7z-compressed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/gzip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gmc-link.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-matroska.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java-jnlp-file.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lha.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-word.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gdbm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gedcom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.calc.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.addin.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.text.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kexiproject-sqlite2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pkcs12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-jbuilder-project.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.impress.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.graphics.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-it87.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kcachegrind.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.formula-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.akonadi.calendar.event.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kolf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.text-web.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.spreadsheet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-magicpoint.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.tcpdump.pcap.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-smb-server.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.text-master.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-turtle.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-access.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/relaxng.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.kplato.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.chart-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ktheme.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkix-crl+pem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.text-flat-xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.notes.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-executable.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gtk-builder.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bzip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cisco-vpn-settings.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-stuffit.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gzpostscript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-khtml-adaptor.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-e-theme.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.presentationml.slideshow.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sqlite3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-dar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-glade.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pef-executable.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bzip-compressed-tar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-profile.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-yaml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-troff-man.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs12+pem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lyx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-theme.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kns.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-karbon.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-zoo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sqlite2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-sunos-news.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tex-gf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gameboy-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ace.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-go-sgf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bittorrent.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cpio.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.calc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cdrdao-toc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ipod-firmware.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.google-earth.kml+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.alarm.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-vfont.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-netcdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-nintendo-ds-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs7-signature.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mobipocket-ebook.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.alarm.archived.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-spkac+base64.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cabri.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-netshow-channel.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-perl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-shellscript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gettext-translation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kgetlist.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-macbinary.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.contactgroup.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tex-pk.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-m4.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-shorten.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkix-pkipath.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-nes-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/msword.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.presentation.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.spreadsheetml.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-webarchive.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-tex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xslt+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/rtf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kchart.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/gml+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lhz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sms-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lrzip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.kugar.mixed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-fictionbook+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-word.template.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-ttf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-compress.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.akonadi.note.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-superkaramba.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gzpdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-shockwave-flash.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-archive.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-wais-source.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-csh.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/illustrator.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.plan.work.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pkcs7-certificates.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openofficeorg.extension.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-toutdoux.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs8+pem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/epub+zip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-wpg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kig.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/msword-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tgif.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kourse.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/winhlp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-t602.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.draw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gba-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kmplot.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-word.document.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java-jce-keystore.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkix-cert.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.scribus.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.visio.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.kde.fontspackage.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-arj.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-core.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mimearchive.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-docbook+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.addin.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/postscript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-xliff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kexi-connectiondata.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pocket-word.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkix-cert+pem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kvtml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-linux-psf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kspread.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkix-crl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.sheet.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lrzip-compressed-tar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-deb.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tuberling.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-alz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cda.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-egon.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-msi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-oleo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-icq.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xspf+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-slp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.base.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cb7.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gnuplot.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kexiproject-sqlite3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-smb-workgroup.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kwordquiz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-xz-compressed-tar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.presentationml.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.presentation-flat-xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-tex-tfm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/zip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cbt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-apple-diskimage.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.corel-draw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-trash.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ole-storage.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kseg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ms-dos-executable.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tarz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.android.package-archive.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs10.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lzop.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs10+pem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gzdvi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.akonadi.calendar.todo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lzip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-class-file.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.slideshow.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/mbox.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bzpdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-aportisdoc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lzma.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-troff-man-compressed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-fluid.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pem-key.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sv4cpio.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/oxps.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-python-bytecode.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-rpm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-libgrx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bzpostscript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-frame.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kword.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.akonadi.collection.virtual.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-amipro.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/octet-stream.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/prs.plucker.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/dicom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-dvi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.presentation-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.emusic-emusic_package.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-krita.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-genesis-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mps.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.sheet.binary.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kword-crypt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.hp-pcl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/mxf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.sheet.binary.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.plan.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/sieve.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kugar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kivio.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gnucash.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kcsrc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/annodex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-wpl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.graphics-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ksysguard.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.draw.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kopete-emoticons.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ksysv-package.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/sdp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.mozilla.xul+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-word.document.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-xpinstall.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-drgeo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.writer.global.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.writer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-xzpdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-smaf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/font-woff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-afm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.alarm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-works.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kwallet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.graphics-flat-xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.symbian.install.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cue.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-hwp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/atom+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-xz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-dbf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-compressed-tar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/mac-binhex40.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-dia-shape.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mif.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-source-rpm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-blender.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.kplato.work.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-dc-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/andrew-inset.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.calc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/smil.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-markaby.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.presentationml.slide.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-word.template.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-framemaker.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.lotus-1-2-3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ustar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.template.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.lotus-wordpro.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mozilla-bookmarks.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.palm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/gnunet-directory.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-arc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.presentationml.presentation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xsd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.draw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-msx-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-wwf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cbr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xhtml+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-quanta.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.impress.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/xml-dtd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.kde.okular-archive.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.hp-hpgl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-siag.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/mathematica.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.presentation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-rar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java-applet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.formula.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-tzo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kgeo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ica.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gz-font-linux-psf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.math.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/metalink+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-gnumeric.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-spkac.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ccmx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/ram.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.impress.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-quicktime-media-link.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs7-mime.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.akonadi.calendar.freebusy.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-accountwizard-package.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/mathml+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-htmlhelp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pkcs8.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pgp-encrypted.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.math.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.text-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-nzb.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sami.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.image.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-qtiplot.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cpio-compressed.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-uml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-iff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-spss-por.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mswinurl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.akonadi.calendar.journal.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cbz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/rss+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.spreadsheet-flat-xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-asp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-zerosize.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-applix-word.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.wordprocessingml.document.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java-pack200.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.wordperfect.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-qw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-spss-sav.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.writer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.template.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-lzma-compressed-tar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ms-shortcut.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-killustrator.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.google-earth.kmz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-php.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-windows-themepack.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.rn-realmedia.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-n64-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-dos.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/pgp-signature.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.template.macroenabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-desktop.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-ufraw.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.chart.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-otf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-excel.sheet.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-cd-image.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-shared-library-la.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-vnd.kde.alarm.active.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-planperfect.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.mail.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.sun.xml.writer.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.spreadsheet-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kformula.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.openxmlformats-officedocument.wordprocessingml.template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-pak.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.kde.kphotoalbum-import.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-navi-animation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-java-archive.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kpovmodeler.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-hwt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-sharedlib.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-mswrite.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-powerpoint.presentation.macroEnabled.12.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.stardivision.chart.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-snf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-speedo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-bzdvi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.oasis.opendocument.database.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.iccprofile.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-quattropro.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.ms-tnef.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kspread-crypt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-trig.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-hdf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-xbel.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/relax-ng-compact-syntax.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-chess-pgn.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-snes-rom.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/ecmascript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-font-ttx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-subrip.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-kudesigner.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/vnd.apple.mpegurl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "application/x-awk.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "model/vrml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/vnd.rn-realaudio.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-speex+ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-matroska.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/basic.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/mp2.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-scpls.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/AMR-WB.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-speex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-stm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-psf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/mpeg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-wavpack.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-riff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-mpegurl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-ms-asx.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-gsm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/aac.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-s3m.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/midi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/AMR.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-iriver-pla.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-xi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-wav.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/ac3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/prs.sid.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-xmf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-musepack.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-aiff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-ms-wma.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/annodex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-aifc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/mp4.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-xm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-wavpack-correction.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-m4b.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-adpcm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-flac+ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-vorbis+ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-amzxml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-tta.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-mod.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-voc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/vnd.dts.hd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-it.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/flac.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/webm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-ape.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-mo3.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-psflib.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-pn-realaudio-plugin.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/vnd.dts.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/x-minipsf.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "audio/ogg.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-vnd.akonadi.socialfeeditem.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-troff-mm.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-vnd.akonadi.socialnotification.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-emacs-lisp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-ooc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.abc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-c++src.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-idl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-adasrc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-katefilelist.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-uuencode.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/tab-separated-values.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-eiffel.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "text/x-apport.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/richtext.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-nfo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/htmlh.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-troff-ms.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-csharp.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vtt.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-cobol.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-makefile.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/sgml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-matlab.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-erlang.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-install.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.graphviz.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/troff.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-java.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-scheme.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-gettext-translation.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-chdr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-bibtex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-changelog.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-vnd.akonadi.note.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-mof.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-ocaml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-microdvd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.trolltech.linguist.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/enriched.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/css.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-scala.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-troff-me.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-texinfo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-cmake.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/cache-manifest.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-patch.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-rpm-spec.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-google-video-pointer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-setext.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-authors.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-xmi.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-objcsrc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-c++hdr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-dcl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-mrml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-ssa.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/rfc822-headers.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-dsrc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-opml+xml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-svhdr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-csrc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-objchdr.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-modelica.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-reject.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-hex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-iptables.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-uri.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-literate-haskell.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-txt2tags.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-lua.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-python.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-vala.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-log.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-fortran.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/plain.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-lilypond.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-sql.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-iMelody.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-xslfo.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-readme.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-ocl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-uil.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.rn-realtext.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-mup.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-subviewer.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-svsrc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vcard.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-markdown.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-vhdl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-credits.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-gettext-translation-template.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.sun.j2me.app-descriptor.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-ldif.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/calendar.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-verilog.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-moc.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-copying.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/xmcd.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-tex.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-qml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.wap.wml.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-dsl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-ms-regedit.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-go.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-pascal.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-tcl.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/spreadsheet.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-mpsub.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/csv.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/x-haskell.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/vnd.wap.wmlscript.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "text/html.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: modified: "x-epoc/x-sisx-app.xml" in xdgdata-mime
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "ffmpegthumbs.desktop" in services
kbuildsycoca4(2653) KBuildSycoca::build: Still in the time dict (i.e. deleted files) ("apps")
kbuildsycoca4(2653) VFolderMenu::pushDocInfo: Menu "debian-menu.menu" not found.
kbuildsycoca4(2653) VFolderMenu::pushDocInfo: Menu "applications-kmenuedit.menu" not found.
kbuildsycoca4(2653) VFolderMenu::processMenu: Processing KDE Legacy dirs for <KDE>
kbuildsycoca4(2653) VFolderMenu::processKDELegacyDirs:
kbuildsycoca4(2653) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "/usr/share/applications/gimp.desktop" in apps
kbuildsycoca4(2653) KConfigGroup::readXdgListEntry: List entry Actions in "/usr/lib/libreoffice/share/xdg/calc.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "/usr/share/applications/bleachbit.desktop" in apps
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "/usr/share/applications/ubuntuone-installer.desktop" in apps
kbuildsycoca4(2653) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/ubuntuone-installer.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "/usr/share/applications/ubuntuone-control-panel-qt-gnome.desktop" in apps
kbuildsycoca4(2653) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/ubuntuone-control-panel-qt-gnome.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "/usr/share/applications/bleachbit-root.desktop" in apps
kbuildsycoca4(2653) KConfigGroup::readXdgListEntry: List entry Actions in "/usr/lib/libreoffice/share/xdg/writer.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(2653) KBuildSycoca::createEntry: new: "/usr/share/applications/vlc.desktop" in apps
kbuildsycoca4(2653) KConfigGroup::readXdgListEntry: List entry Actions in "/usr/lib/libreoffice/share/xdg/math.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(2653) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "kerfuffle_libarchive_readonly.desktop" specifies undefined mimetype/servicetype "application/x-servicepack"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "plasma-kpart.desktop" specifies undefined mimetype/servicetype "KParts/Part"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "fontthumbnail.desktop" specifies undefined mimetype/servicetype "fonts/package"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "application/csv"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "application/excel"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "application/tab-separated-values"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "application/x-dos_ms_excel"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "application/x-excel"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "application/x-ms-excel"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/calc.desktop" specifies undefined mimetype/servicetype "text/comma-separated-values"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/x-gimp-gbr"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/x-gimp-pat"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/x-gimp-gih"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/x-psp"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/software-properties-kde.desktop" specifies undefined mimetype/servicetype "text/x-apt-sources-list"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/installfont.desktop" specifies undefined mimetype/servicetype "fonts/package"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/amarok_append.desktop" specifies undefined mimetype/servicetype "audio/*"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amarok.desktop" specifies undefined mimetype/servicetype "application/x-ogm-audio"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amzdownloader.desktop" specifies undefined mimetype/servicetype "audio/x-amzaudio"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/ark_servicemenu.desktop" specifies undefined mimetype/servicetype "application/x-servicepack"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/ark_servicemenu.desktop" specifies undefined mimetype/servicetype "application/lha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/ark_servicemenu.desktop" specifies undefined mimetype/servicetype "application/maclha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/gwenview.desktop" specifies undefined mimetype/servicetype "image/x-webp"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "kfontviewpart.desktop" specifies undefined mimetype/servicetype "fonts/package"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.stardivision.writer-global"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/lib/libreoffice/share/xdg/writer.desktop" specifies undefined mimetype/servicetype "application/x-extension-txt"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ark_dndextract.desktop" specifies undefined mimetype/servicetype "application/x-servicepack"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ark_dndextract.desktop" specifies undefined mimetype/servicetype "application/lha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ark_dndextract.desktop" specifies undefined mimetype/servicetype "application/maclha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "amarok_collection-playdarcollection.desktop" specifies undefined mimetype/servicetype "Amarok/Plugin-disabled"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "windowsexethumbnail.desktop" specifies undefined mimetype/servicetype "application/x-msdownload"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ffmpegthumbs.desktop" specifies undefined mimetype/servicetype "video/*"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "imagethumbnail.desktop" specifies undefined mimetype/servicetype "image/x-webp"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ark_part.desktop" specifies undefined mimetype/servicetype "application/x-servicepack"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ark_part.desktop" specifies undefined mimetype/servicetype "application/lha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "ark_part.desktop" specifies undefined mimetype/servicetype "application/maclha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "gvpart.desktop" specifies undefined mimetype/servicetype "image/x-webp"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/ark.desktop" specifies undefined mimetype/servicetype "application/x-servicepack"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/ark.desktop" specifies undefined mimetype/servicetype "application/lha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/ark.desktop" specifies undefined mimetype/servicetype "application/maclha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "video/mkv"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/aiff"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-basic"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/8svx"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/168sv"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "image/ilbm"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "video/anim"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "video/mng"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "phononbackends/gstreamer.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "kerfuffle_clilha.desktop" specifies undefined mimetype/servicetype "application/lha"
kbuildsycoca4(2653) KBuildServiceFactory::populateServiceTypes: "kerfuffle_clilha.desktop" specifies undefined mimetype/servicetype "application/maclha"
kbuildsycoca4(2653) KBuildSycoca::save: Saving
kbuildsycoca4(2653) kdemain: Emitting notifyDatabaseChanged ("xdgdata-mime", "services", "apps", "apps")
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.kde/share/config/activitymanager-pluginsrc
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
QObject::connect: Cannot connect (null)::resourceScoreUpdated(QString, QString, QString, double) to NepomukPlugin::resourceScoreUpdated(QString, QString, QString, double)
QObject::connect: Cannot connect (null)::recentStatsDeleted(QString, int, QString) to NepomukPlugin::deleteRecentStats(QString, int, QString)
QObject::connect: Cannot connect (null)::earlierStatsDeleted(QString, int) to NepomukPlugin::deleteEarlierStats(QString, int)
kactivitymanagerd(2658)/nepomuk (library): Could not find virtuoso to connect to. Aborting
```

---

### Post by dave2001 on 2014-02-11
anyone care to chime in?

---

### Post by Dave_L on 2014-02-11
Aside from the messages, does the application, e.g. kwrite, work properly?

If so, I would ignore the messages. But that's just my opinion, not a definitive answer.

---

### Post by Frogs Hair on 2014-02-11
Errors are fairly common when opening graphical applications as root . I am not KDE user , but in Gnome the errors can be theme or icon related .  Example:```
 gksu gedit

(gksu:14892): Gtk-WARNING **: Theme directory actions/16 of theme malys-uniblue has no size field
``` The error repeats a number of times before the application opens and refers to the icon set.

---

### Post by dave2001 on 2014-02-16
Thanks for the input!  Sounds like it might be one of those "quirks" of ubuntu being so gung-ho on sudo this or sudo that. 

I'd love a more definitive and final answer if anyone out there in cyberland has a one.

---

### Post by bab1 on 2014-02-16
> **dave2001 said:**
> Thanks for the input!  Sounds like it might be one of those "quirks" of ubuntu being so gung-ho on sudo this or sudo that. 

I'd love a more definitive and final answer if anyone out there in cyberland has a one.

It's not really a quirk.  It's because you are opening a GUI application in a terminal.  It has nothing to do with sudo or gksudo or being the root user.

Try opening a GUI type editor in the terminal with you as the user (no sudo or gksudo) and you will see the same error messages.

---

### Post by Frogs Hair on 2014-02-16
> **bab1 said:**
> It's not really a quirk.  It's because you are opening a GUI application in a terminal.  It has nothing to do with sudo or gksudo or being the root user.

Try opening a GUI type editor in the terminal with you as the user (no sudo or gksudo) and you will see the same error messages.


Very true , because I don't open applications from the terminal with the exception of gksudo nautilus and gedit I only see GTK or icon errors when using those two.

---

### Post by bab1 on 2014-02-16
> **Frogs Hair said:**
> Very true , because I don't open applications from the terminal with the exception of gksudo nautilus and gedit I only see errors when using those two.
Also, here are no errors when opening via GUI because the app can find the libs it expects to see.  ;-)

---

