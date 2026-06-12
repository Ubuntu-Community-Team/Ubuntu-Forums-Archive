---
title: "Amavis - spamassassin"
date: 2015-09-11
forum: General Help
---

### Post by jakub17 on 2015-09-11
Hello,

When message is marked as SPAM, message is not delivered to mailbox. I don't know what happen to message, I can't see it in log. Any suggestions?

Amavis normally detect spamassassin, it looks working great.
```
  1 Sep 11 11:47:14.839 mail.myserver.com /usr/sbin/amavisd-new[11496]: Using internal spam scanner code for SpamAssassin                                                                                                                
Sep 11 11:47:14.839 mail.myserver.com /usr/sbin/amavisd-new[11496]: Deleting db files snmp.db,nanny.db,__db.002,__db.001,__db.003 in /var/lib/amavis/db                                                                              
Sep 11 11:47:14.841 mail.myserver.com /usr/sbin/amavisd-new[11496]: Creating db in /var/lib/amavis/db/; BerkeleyDB 0.54, libdb 5.3                                                                                                    
Sep 11 11:47:14.847 mail.myserver.com /usr/sbin/amavisd-new[11496]: initializing Mail::SpamAssassin (0)                                                                                                                              
Sep 11 11:47:14.847 mail.myserver.com /usr/sbin/amavisd-new[11496]: SpamAssassin debug facilities: info                                                                                                                              
Sep 11 11:47:16.631 mail.myserver.com /usr/sbin/amavisd-new[11496]: SpamAssassin loaded plugins: AskDNS, AutoLearnThreshold, Bayes, BodyEval, Check, DKIM, DNSEval, FreeMail, HTMLEval, HTTPSMismatch, Hashcash, HeaderEval, ImageInfo    , MIMEEval, MIMEHeader, Pyzor, Razor2, RelayEval, ReplaceTags, SPF, SpamCop, URIDNSBL, URIDetail, URIEval, VBounce, WLBLEval, WhiteListSubject                                                                                        
Sep 11 11:47:16.631 mail.myserver.com /usr/sbin/amavisd-new[11496]: SpamControl: init_pre_fork on SpamAssassin done                                                                                                                  
Sep 11 11:47:16.632 mail.myserver.com /usr/sbin/amavisd-new[11496]: extra modules loaded after daemonizing/chrooting: /etc/perl/Net/libnet.cfg, Mail/SpamAssassin/Plugin/FreeMail.pm, Mail/SpamAssassin/Plugin/SpamCop.pm, Net/Cmd.pm,     Net/Config.pm, Net/SMTP.pm                                                                                                                                                                                                          
Sep 11 11:47:16.632 mail.myserver.com /usr/sbin/amavisd-new[11496]: Net::Server: Beginning prefork (2 processes)                                                                                                                      
Sep 11 11:47:16.632 mail.myserver.com /usr/sbin/amavisd-new[11496]: Net::Server: Starting "2" children                                                                                                                                
Sep 11 11:47:16.693 mail.myserver.com /usr/sbin/amavisd-new[11503]: Net::Server: Child Preforked (11503)                                                                                                                              
Sep 11 11:47:16.694 mail.myserver.com /usr/sbin/amavisd-new[11503]: entered child_init_hook                                                                                                                                          
Sep 11 11:47:16.708 mail.myserver.com /usr/sbin/amavisd-new[11503]: SpamControl: init_child on SpamAssassin done                                                                                                                      
Sep 11 11:47:16.740 mail.myserver.com /usr/sbin/amavisd-new[11496]: Net::Server: Parent ready for children.                                                                                                                          
Sep 11 11:47:16.741 mail.myserver.com /usr/sbin/amavisd-new[11504]: Net::Server: Child Preforked (11504)                                                                                                                              
Sep 11 11:47:16.742 mail.myserver.com /usr/sbin/amavisd-new[11504]: entered child_init_hook                                                                                                                                          
Sep 11 11:47:16.753 mail.myserver.com /usr/sbin/amavisd-new[11504]: SpamControl: init_child on SpamAssassin done                                                                                                                      

```
But my problem is that spam test
```
echo "XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X" | mutt -s "zero day" -- recipient@myserver.com
```
Message is not delivered into mailbox (recipient@myserver.com). In Amavis debug I can see that message was marked as SPAM, which is correct:
```
Sep 11 11:52:20.516 binary-rose.roses.org /usr/sbin/amavisd-new[11503]: (11503-01) header_edits_for_quar: <out@gmail.com> -> <recipient@myserver.com>, Yes, score=1000 tag=2 tag2=6.31 kill=6.31 tests=[GTUBE=1000] autolearn=no autolearn_fo
rce=no
Sep 11 11:52:20.517 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header encoded (all-ASCII): X-Spam-Flag: YES
Sep 11 11:52:20.517 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header: X-Spam-Flag: YES\n
Sep 11 11:52:20.517 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header encoded (all-ASCII): X-Spam-Score: 1000
Sep 11 11:52:20.517 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header: X-Spam-Score: 1000\n
Sep 11 11:52:20.517 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header encoded (all-ASCII): X-Spam-Level: ****************************************************************
Sep 11 11:52:20.517 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header: X-Spam-Level: ****************************************************************\n
Sep 11 11:52:20.518 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header encoded (all-ASCII): X-Spam-Status: Yes,\n score=1000\n tag=2\n tag2=6.31\n kill=6.31\n tests=[GTUBE=1000]\n autolearn=no autolearn_force=no
Sep 11 11:52:20.518 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) header: X-Spam-Status: Yes, score=1000 tag=2 tag2=6.31 kill=6.31 tests=[GTUBE=1000]\n\tautolearn=no autolearn_force=no\n
Sep 11 11:52:20.518 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) quar: scanner provided a header field X-Spam-Checker-Version, inhibited by %allowed_added_header_fields
Sep 11 11:52:20.519 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) quar: scanner provided a header field X-Spam-Flag, but we preferred our own
Sep 11 11:52:20.519 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) quar: scanner provided a header field X-Spam-Level, but we preferred our own
Sep 11 11:52:20.519 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) quar: scanner provided a header field X-Spam-Status, but we preferred our own
Sep 11 11:52:20.519 mail.myserver.com /usr/sbin/amavisd-new[11503]: (11503-01) do_notify_and_quarantine: quarantine spam-quarantine

```
For to be sure everybody undesrtand I'll explain again: my host is mail.myserver.com, and spam was sent from [EMAIL="out@gmail.com"]out@gmail.com[/EMAIL], recipient was [EMAIL="recipient@myserver.com"]recipient@myserver.com[/EMAIL].

Here is complete debug of amavis, (amavids-new debug):
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US:en",
    LC_ALL = (unset),
    LC_PAPER = "cs_CZ.UTF-8",
    LC_ADDRESS = "cs_CZ.UTF-8",
    LC_MONETARY = "cs_CZ.UTF-8",
    LC_NUMERIC = "cs_CZ.UTF-8",
    LC_TELEPHONE = "cs_CZ.UTF-8",
    LC_IDENTIFICATION = "cs_CZ.UTF-8",
    LC_MEASUREMENT = "cs_CZ.UTF-8",
    LC_TIME = "cs_CZ.UTF-8",
    LC_NAME = "cs_CZ.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
Sep 11 11:56:27.521 mail.myserver.com /usr/sbin/amavisd-new[11699]: logging initialized, log level 1, syslog: amavis.mail
Sep 11 11:56:27.522 mail.myserver.com /usr/sbin/amavisd-new[11699]: starting. /usr/sbin/amavisd-new at mail.myserver.com amavisd-new-2.10.1 (20141025), Unicode aware, LANG="en_US.UTF-8"
Sep 11 11:56:27.522 mail.myserver.com /usr/sbin/amavisd-new[11699]: perl=5.020002, user=, EUID: 121 (121);  group=, EGID: 132 132 (132 132)
Sep 11 11:56:27.590 mail.myserver.com /usr/sbin/amavisd-new[11699]: INFO: no optional modules: unicore::lib::Perl::SpacePer.pl unicore::lib::Nt::De.pl Unix::Getrusage
Sep 11 11:56:27.590 mail.myserver.com /usr/sbin/amavisd-new[11699]: SpamControl: attempting to load scanner SpamAssassin, module Amavis::SpamControl::SpamAssassin
Sep 11 11:56:27.590 mail.myserver.com /usr/sbin/amavisd-new[11699]: SpamControl: scanner SpamAssassin, module Amavis::SpamControl::SpamAssassin
Sep 11 11:56:27.996 mail.myserver.com /usr/sbin/amavisd-new[11699]: INFO: SA version: 3.4.0, 3.004000, no optional modules: Net::CIDR::Lite Encode::Detect Razor2::Client::Agent Image::Info Image::Info::GIF Image::Info::JPEG Image::Info::PNG Image::Info::BMP Image::Info::TIFF
Sep 11 11:56:27.996 mail.myserver.com /usr/sbin/amavisd-new[11699]: SpamControl: init_pre_chroot on SpamAssassin done
Sep 11 11:56:27.996 mail.myserver.com /usr/sbin/amavisd-new[11699]: socket module IO::Socket::IP, protocol families available: INET, INET6
Sep 11 11:56:27.997 mail.myserver.com /usr/sbin/amavisd-new[11699]: bind to /var/lib/amavis/amavisd.sock|unix, 127.0.0.1:10024/tcp, [::1]:10024/tcp
Sep 11 11:56:27.998 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: 2015/09/11-11:56:27 Amavis (type Net::Server::PreForkSimple) starting! pid(11699)
Sep 11 11:56:28.003 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Binding to UNIX socket file "/var/lib/amavis/amavisd.sock"
Sep 11 11:56:28.003 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Binding to TCP port 10024 on host 127.0.0.1 with IPv4
Sep 11 11:56:28.004 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Binding to TCP port 10024 on host ::1 with IPv6
Sep 11 11:56:28.005 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Group Not Defined.  Defaulting to EGID '132 132'
Sep 11 11:56:28.005 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: User Not Defined.  Defaulting to EUID '121'
Sep 11 11:56:28.005 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Setting up serialization via flock
Sep 11 11:56:28.006 mail.myserver.com /usr/sbin/amavisd-new[11699]: after_chroot_init: EUID: 121 (121);  EGID: 132 132 (132 132)
Sep 11 11:56:28.006 mail.myserver.com /usr/sbin/amavisd-new[11699]: config files read: /usr/share/amavis/conf.d/10-debian_scripts, /usr/share/amavis/conf.d/20-package, /etc/amavis/conf.d/01-debian, /etc/amavis/conf.d/05-domain_id, /etc/amavis/conf.d/05-node_id, /etc/amavis/conf.d/15-av_scanners, /etc/amavis/conf.d/15-content_filter_mode, /etc/amavis/conf.d/20-debian_defaults, /etc/amavis/conf.d/25-amavis_helpers, /etc/amavis/conf.d/30-template_localization, /etc/amavis/conf.d/50-user, /etc/amavis/conf.d/60-debug
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Amavis::Conf        2.404
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Archive::Zip        1.39
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module BerkeleyDB          0.54
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Compress::Raw::Zlib 2.065
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Compress::Zlib      2.064
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Crypt::OpenSSL::RSA 0.28
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module DB_File             1.831
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Digest::MD5         2.53
Sep 11 11:56:28.026 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Digest::SHA         5.88
Sep 11 11:56:28.027 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Encode              2.60
Sep 11 11:56:28.027 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module File::Temp          0.2304
Sep 11 11:56:28.027 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module IO::Socket::INET6   2.72
Sep 11 11:56:28.027 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module IO::Socket::IP      0.29
Sep 11 11:56:28.027 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module MIME::Entity        5.505
Sep 11 11:56:28.027 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module MIME::Parser        5.505
Sep 11 11:56:28.028 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module MIME::Tools         5.505
Sep 11 11:56:28.028 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Mail::DKIM::Verifier 0.4
Sep 11 11:56:28.028 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Mail::Header        2.13
Sep 11 11:56:28.028 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Mail::Internet      2.13
Sep 11 11:56:28.028 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Mail::SPF           v2.009
Sep 11 11:56:28.028 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Mail::SpamAssassin  3.004000
Sep 11 11:56:28.029 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Net::DNS            0.81
Sep 11 11:56:28.029 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Net::LibIDN         0.12
Sep 11 11:56:28.029 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Net::Server         2.008
Sep 11 11:56:28.030 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module NetAddr::IP         4.075
Sep 11 11:56:28.030 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Scalar::Util        1.38
Sep 11 11:56:28.030 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Socket              2.013
Sep 11 11:56:28.030 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Socket6             0.25
Sep 11 11:56:28.030 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Time::HiRes         1.9726
Sep 11 11:56:28.030 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module URI                 1.64
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: Module Unix::Syslog        1.1
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: Amavis::ZMQ code     NOT loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: Amavis::DB code      loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: SQL base code        NOT loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: SQL::Log code        NOT loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: SQL::Quarantine      NOT loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: Lookup::SQL code     NOT loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: Lookup::LDAP code    NOT loaded
Sep 11 11:56:28.031 mail.myserver.com /usr/sbin/amavisd-new[11699]: AM.PDP-in proto code loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: SMTP-in proto code   loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: Courier proto code   NOT loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: SMTP-out proto code  loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: Pipe-out proto code  NOT loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: BSMTP-out proto code NOT loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: Local-out proto code loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: OS_Fingerprint code  NOT loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: ANTI-VIRUS code      loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: ANTI-SPAM code       loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: ANTI-SPAM-EXT code   NOT loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: ANTI-SPAM-C code     NOT loaded
Sep 11 11:56:28.032 mail.myserver.com /usr/sbin/amavisd-new[11699]: ANTI-SPAM-SA code    loaded
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: Unpackers code       loaded
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: DKIM code            NOT loaded
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: Tools code           NOT loaded
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found $file            at /usr/bin/file
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found $altermime       at /usr/bin/altermime
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: Internal decoder for .mail
Sep 11 11:56:28.033 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .Z    at /bin/uncompress
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .gz   at /bin/gzip -d
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: Internal decoder for .gz   (backup, not used)
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .bz2  at /bin/bzip2 -d
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .xz   at /usr/bin/xz -dc
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .lzma at /usr/bin/xz -dc --format=lzma
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: No ext program for   .lrz, tried: lrzip -q -k -d -o -, lrzcat -q -k
Sep 11 11:56:28.034 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .lzo  at /usr/bin/lzop -d
Sep 11 11:56:28.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: No ext program for   .lz4, tried: lz4c -d
Sep 11 11:56:28.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .rpm  at /usr/bin/rpm2cpio
Sep 11 11:56:28.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .cpio at /bin/pax
Sep 11 11:56:28.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .tar  at /bin/pax
Sep 11 11:56:28.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .deb  at /usr/bin/ar
Sep 11 11:56:28.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .rar  at /usr/bin/unrar-free
Sep 11 11:56:28.036 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .arj  at /usr/bin/arj
Sep 11 11:56:28.036 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .arc  at /usr/bin/nomarch
Sep 11 11:56:28.036 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .zoo  at /usr/bin/zoo
Sep 11 11:56:28.036 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .doc  at /usr/bin/ripole
Sep 11 11:56:28.036 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .cab  at /usr/bin/cabextract
Sep 11 11:56:28.036 mail.myserver.com /usr/sbin/amavisd-new[11699]: Internal decoder for .tnef
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .zip  at /usr/bin/7za
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .kmz  at /usr/bin/7za
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Internal decoder for .zip  (backup, not used)
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Internal decoder for .kmz  (backup, not used)
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .7z   at /usr/bin/7zr
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .gz   at /usr/bin/7za (backup, not used)
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .bz2  at /usr/bin/7za (backup, not used)
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .Z    at /usr/bin/7za (backup, not used)
Sep 11 11:56:28.037 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .tar  at /usr/bin/7za (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .xz   at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .lzma at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .jar  at /usr/bin/7z
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .cpio at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .arj  at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .rar  at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .swf  at /usr/bin/7z
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .lha  at /usr/bin/7z
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .iso  at /usr/bin/7z
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .cab  at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .deb  at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.038 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .rpm  at /usr/bin/7z (backup, not used)
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found decoder for    .exe  at /usr/bin/unrar-free; /usr/bin/arj
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: No decoder for       .F  
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: No decoder for       .lrz
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: No decoder for       .lz4
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: Using primary internal av scanner code for ClamAV-clamd
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: KasperskyLab AVP - aveclient
Sep 11 11:56:28.039 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: KasperskyLab AntiViral Toolkit Pro (AVP)
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: KasperskyLab AVPDaemonClient
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: CentralCommand Vexira (new) vascan
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Avira AntiVir
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Command AntiVirus for Linux
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Symantec CarrierScan via Symantec CommandLineScanner
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Symantec AntiVirus Scan Engine
Sep 11 11:56:28.040 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: F-Secure Antivirus for Linux servers
Sep 11 11:56:28.041 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: CAI InoculateIT
Sep 11 11:56:28.041 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: CAI eTrust Antivirus
Sep 11 11:56:28.041 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: MkS_Vir for Linux (beta)
Sep 11 11:56:28.041 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: MkS_Vir daemon
Sep 11 11:56:28.041 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: ESET Software ESETS Command Line Interface
Sep 11 11:56:28.041 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: ESET NOD32 for Linux File servers
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Norman Virus Control v5 / Linux
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Panda CommandLineSecure 9 for Linux
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: NAI McAfee AntiVirus (uvscan)
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: VirusBuster
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: CyberSoft VFind
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: avast! Antivirus
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: Ikarus AntiVirus for Linux
Sep 11 11:56:28.042 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: BitDefender
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: BitDefender
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: No primary av scanner: ArcaVir for Linux
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: Found secondary av scanner ClamAV-clamscan at /usr/bin/clamscan
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: No secondary av scanner: F-PROT Antivirus for UNIX
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: No secondary av scanner: FRISK F-Prot Antivirus
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: No secondary av scanner: Trend Micro FileScanner
Sep 11 11:56:28.043 mail.myserver.com /usr/sbin/amavisd-new[11699]: No secondary av scanner: drweb - DrWeb Antivirus
Sep 11 11:56:28.044 mail.myserver.com /usr/sbin/amavisd-new[11699]: No secondary av scanner: Kaspersky Antivirus v5.5
Sep 11 11:56:28.044 mail.myserver.com /usr/sbin/amavisd-new[11699]: Using internal spam scanner code for SpamAssassin
Sep 11 11:56:28.044 mail.myserver.com /usr/sbin/amavisd-new[11699]: Deleting db files snmp.db,nanny.db,__db.002,__db.001,__db.003 in /var/lib/amavis/db
Sep 11 11:56:28.046 mail.myserver.com /usr/sbin/amavisd-new[11699]: Creating db in /var/lib/amavis/db/; BerkeleyDB 0.54, libdb 5.3
Sep 11 11:56:28.050 mail.myserver.com /usr/sbin/amavisd-new[11699]: initializing Mail::SpamAssassin (0)
Sep 11 11:56:28.051 mail.myserver.com /usr/sbin/amavisd-new[11699]: SpamAssassin debug facilities: info
Sep 11 11:56:29.915 mail.myserver.com /usr/sbin/amavisd-new[11699]: SpamAssassin loaded plugins: AskDNS, AutoLearnThreshold, Bayes, BodyEval, Check, DKIM, DNSEval, FreeMail, HTMLEval, HTTPSMismatch, Hashcash, HeaderEval, ImageInfo, MIMEEval, MIMEHeader, Pyzor, Razor2, RelayEval, ReplaceTags, SPF, SpamCop, URIDNSBL, URIDetail, URIEval, VBounce, WLBLEval, WhiteListSubject
Sep 11 11:56:29.915 mail.myserver.com /usr/sbin/amavisd-new[11699]: SpamControl: init_pre_fork on SpamAssassin done
Sep 11 11:56:29.915 mail.myserver.com /usr/sbin/amavisd-new[11699]: extra modules loaded after daemonizing/chrooting: /etc/perl/Net/libnet.cfg, Mail/SpamAssassin/Plugin/FreeMail.pm, Mail/SpamAssassin/Plugin/SpamCop.pm, Net/Cmd.pm, Net/Config.pm, Net/SMTP.pm
Sep 11 11:56:29.916 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Beginning prefork (2 processes)
Sep 11 11:56:29.916 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Starting "2" children
Sep 11 11:56:29.984 mail.myserver.com /usr/sbin/amavisd-new[11707]: Net::Server: Child Preforked (11707)
Sep 11 11:56:29.985 mail.myserver.com /usr/sbin/amavisd-new[11707]: entered child_init_hook
Sep 11 11:56:29.998 mail.myserver.com /usr/sbin/amavisd-new[11707]: SpamControl: init_child on SpamAssassin done
Sep 11 11:56:30.035 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Parent ready for children.
Sep 11 11:56:30.036 mail.myserver.com /usr/sbin/amavisd-new[11708]: Net::Server: Child Preforked (11708)
Sep 11 11:56:30.037 mail.myserver.com /usr/sbin/amavisd-new[11708]: entered child_init_hook
Sep 11 11:56:30.050 mail.myserver.com /usr/sbin/amavisd-new[11708]: SpamControl: init_child on SpamAssassin done
Sep 11 11:56:37.004 mail.myserver.com /usr/sbin/amavisd-new[11707]: Net::Server: 2015/09/11-11:56:36 CONNECT TCP Peer: "[127.0.0.1]:53638" Local: "[127.0.0.1]:10024"
Sep 11 11:56:37.009 mail.myserver.com /usr/sbin/amavisd-new[11707]: loaded base policy bank
Sep 11 11:56:37.011 mail.myserver.com /usr/sbin/amavisd-new[11707]: lookup_ip_acl (inet_acl) arr.obj: key="127.0.0.1" matches "127.0.0.1", result=1
Sep 11 11:56:37.012 mail.myserver.com /usr/sbin/amavisd-new[11707]: process_request: fileno sock=13, STDIN=0, STDOUT=1
Sep 11 11:56:37.012 mail.myserver.com /usr/sbin/amavisd-new[11707]: get_deadline switch_to_my_time(new request) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.012 mail.myserver.com /usr/sbin/amavisd-new[11707]: prolong_timer switch_to_my_time(new request): timer 288, was 0, deadline in 480.0 s
Sep 11 11:56:37.015 mail.myserver.com /usr/sbin/amavisd-new[11707]: process_request: suggested_protocol="" on a TCP socket
Sep 11 11:56:37.018 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) SMTP> 220 [127.0.0.1] ESMTP amavisd-new service ready
Sep 11 11:56:37.019 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.019 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 4: was busy, 14.4 ms, total idle 0.000 s, busy 0.014 s
Sep 11 11:56:37.019 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) smtp readline: read 28 bytes, new size: 28
Sep 11 11:56:37.020 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.7 ms, total idle 0.001 s, busy 0.014 s
Sep 11 11:56:37.020 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) SMTP< LHLO mail.myserver.com\r\n
Sep 11 11:56:37.020 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP LHLO) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.020 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP LHLO): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.022 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-[127.0.0.1]
Sep 11 11:56:37.022 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-VRFY
Sep 11 11:56:37.022 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-PIPELINING
Sep 11 11:56:37.022 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-SIZE
Sep 11 11:56:37.022 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-ENHANCEDSTATUSCODES
Sep 11 11:56:37.023 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-8BITMIME
Sep 11 11:56:37.023 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-SMTPUTF8
Sep 11 11:56:37.023 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250-DSN
Sep 11 11:56:37.023 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250 XFORWARD NAME ADDR PORT PROTO HELO IDENT SOURCE
Sep 11 11:56:37.023 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.024 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 6: was busy, 4.2 ms, total idle 0.001 s, busy 0.019 s
Sep 11 11:56:37.024 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) smtp readline: read 254 bytes, new size: 254
Sep 11 11:56:37.025 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.8 ms, total idle 0.001 s, busy 0.019 s
Sep 11 11:56:37.025 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< XFORWARD NAME=li1359-38.members.linode.com ADDR=139.162.196.38 PORT=38301\r\n
Sep 11 11:56:37.025 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP XFORWARD) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.025 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP XFORWARD): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.026 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250 2.5.0 Ok XFORWARD
Sep 11 11:56:37.026 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.026 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 6: was busy, 1.7 ms, total idle 0.001 s, busy 0.020 s
Sep 11 11:56:37.026 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.2 ms, total idle 0.002 s, busy 0.020 s
Sep 11 11:56:37.027 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< XFORWARD PROTO=ESMTP HELO=mail.gmail.com IDENT=EA60D7926B8 SOURCE=REMOTE\r\n
Sep 11 11:56:37.027 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP XFORWARD) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.027 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP XFORWARD): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.027 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250 2.5.0 Ok XFORWARD
Sep 11 11:56:37.028 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.028 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 6: was busy, 1.3 ms, total idle 0.002 s, busy 0.022 s
Sep 11 11:56:37.028 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.2 ms, total idle 0.002 s, busy 0.022 s
Sep 11 11:56:37.028 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< MAIL FROM:<out@gmail.com> SIZE=696\r\n
Sep 11 11:56:37.028 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP MAIL) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.028 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP MAIL): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.029 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) check_mail_begin_task: task_count=1
Sep 11 11:56:37.030 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) TempDir::prepare_dir: created directory /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV
Sep 11 11:56:37.030 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) TempDir::prepare_file: creating file /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/email.txt
Sep 11 11:56:37.031 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) TempDir::prepare_file: layers: unix,perlio
Sep 11 11:56:37.031 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_ip_acl (client_ipaddr_policy) arr.obj: key="139.162.196.38", no match
Sep 11 11:56:37.032 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [debug_sender] => undef, "out@gmail.com" does not match
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) mesage size set to a declared size 696
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250 2.1.0 Sender <out@gmail.com> OK
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 6: was busy, 5.1 ms, total idle 0.002 s, busy 0.027 s
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.2 ms, total idle 0.002 s, busy 0.027 s
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< RCPT TO:<recipient@myserver.com> ORCPT=rfc822;recipient@myserver.com\r\n
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP RCPT) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.033 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP RCPT): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.034 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup => undef, "recipient@myserver.com", no lookup tables
Sep 11 11:56:37.034 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250 2.1.5 Recipient <recipient@myserver.com> OK
Sep 11 11:56:37.034 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.034 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 6: was busy, 1.3 ms, total idle 0.002 s, busy 0.028 s
Sep 11 11:56:37.035 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.1 ms, total idle 0.002 s, busy 0.028 s
Sep 11 11:56:37.035 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< DATA\r\n
Sep 11 11:56:37.035 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP DATA) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.035 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP DATA): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.036 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP [127.0.0.1]:10024 /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV: <out@gmail.com> -> <recipient@myserver.com> SIZE=696 Received: from mail.myserver.com ([127.0.0.1]) by localhost (mail.myserver.com [127.0.0.1]) (amavisd-new, port 10024) with LMTP for <recipient@myserver.com>; Fri, 11 Sep 2015 11:56:37 +0000 (UTC)
Sep 11 11:56:37.036 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 354 End data with <CR><LF>.<CR><LF>
Sep 11 11:56:37.036 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:37.036 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, receiving data
Sep 11 11:56:37.067 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) smtp copy: read 705 bytes into buffer, new size: 705
Sep 11 11:56:37.067 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) smtp copy: 6 bytes still buffered at end
Sep 11 11:56:37.067 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx data-end) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.068 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx data-end): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:37.068 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< .<CR><LF>
Sep 11 11:56:37.069 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline get_body_digest - deadline in 480.0 s, set to 30.000 s
Sep 11 11:56:37.069 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline digest_pre - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.069 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer digest_pre: timer 288, was 288, deadline in 480.0 s
Sep 11 11:56:37.070 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_body_digest: reading header section from memory
Sep 11 11:56:37.070 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline digest_hdr - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer digest_hdr: timer 288, was 288, deadline in 480.0 s
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_body_digest: reading mail body from memory, 0 DKIM signatures
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline digest_body - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer digest_body: timer 288, was 288, deadline in 480.0 s
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_body_digest: message size 696, header+sep 626, body 70
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) body type (8bit-MIMEtransport): unlabeled, good (h=0, b=0)
Sep 11 11:56:37.071 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) body hash: 0fca00f17d26a0b7bf2f91aed000ec3b
Sep 11 11:56:37.073 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) ip_from_received: 139.162.196.38
Sep 11 11:56:37.074 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) ip_from_received: no IP address in:  by mail.gmail.com (Postfix, from userid 0)\n\tid E68D8206EB; Fri, 11 Sep 2015 11:56:35 +0000 (UTC)\n
Sep 11 11:56:37.075 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_ip_acl (public_nets) arr.obj: key="127.0.0.1" matches "!127.0.0.0/8", result=0
Sep 11 11:56:37.075 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_ip_acl (public_nets) arr.obj: key="139.162.196.38" matches "::ffff:0:0/96", result=1
Sep 11 11:56:37.075 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) trace: LMTP://[127.0.0.1]:53638 < ESMTPS://[139.162.196.38]:38301 < x
Sep 11 11:56:37.076 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Original mail size: 696; quota set to: 348000 bytes (fmin=5, fmax=500, qmin=102400, qmax=314572800)
Sep 11 11:56:37.077 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Checking: ja7aIXNm4vr5 [139.162.196.38] <out@gmail.com> -> <recipient@myserver.com>
Sep 11 11:56:37.077 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) 2822.From: <root@mail.gmail.com>, 2821.Mail_From: <out@gmail.com>
Sep 11 11:56:37.077 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_acl(recipient@myserver.com), no match
Sep 11 11:56:37.077 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [local_domains] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.078 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [bypass_virus_checks] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.078 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [bypass_banned_checks] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.078 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [bypass_spam_checks] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.078 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Open relay? Nonlocal recips but not originating: recipient@myserver.com
Sep 11 11:56:37.081 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Extracting mime components from a string
Sep 11 11:56:37.092 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Issued a new file name: p001
Sep 11 11:56:37.095 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Charging 69 bytes to remaining quota 348000 (out of 348000, (0%)) - by mime_decode
Sep 11 11:56:37.095 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) p001 1 Content-Type: text/plain, size: 69 B, name:
Sep 11 11:56:37.096 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline mime_decode - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.096 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer mime_decode: timer 288, was 288, deadline in 480.0 s
Sep 11 11:56:37.097 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline mime_decode-1 - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:37.097 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer mime_decode-1: timer 288, was 288, deadline in 480.0 s
Sep 11 11:56:37.097 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) decode_parts: level=1, #parts=1 : p001
Sep 11 11:56:37.097 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) running file(1) on 1 files, arglist size 18
Sep 11 11:56:37.149 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) run_command: [11720] /usr/bin/file p001 </dev/null 2>&1
Sep 11 11:56:37.177 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) result line from file(1): p001: ASCII text\n
Sep 11 11:56:37.178 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_re("ASCII text") matches key "(?^i:^(ASCII|text)\\b)", result="asc"
Sep 11 11:56:37.179 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [map_full_type_to_short_type] => true,  "ASCII text" matches, result="asc", matching_key="(?^i:^(ASCII|text)\\b)"
Sep 11 11:56:37.179 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) File-type of p001: ASCII text; (asc)
Sep 11 11:56:37.180 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) decompose_part: p001 - atomic
Sep 11 11:56:37.180 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline parts_decode - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.180 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer parts_decode: timer 288, was 288, deadline in 479.9 s
Sep 11 11:56:37.180 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [bypass_header_checks] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.181 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) check_header: 0, OK
Sep 11 11:56:37.181 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [bypass_header_checks] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.181 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Checking for banned types and filenames
Sep 11 11:56:37.181 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="DEFAULT"
Sep 11 11:56:37.181 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [banned_filename], 1 matches for "recipient@myserver.com", results: "(constant:DEFAULT)"=>"DEFAULT"
Sep 11 11:56:37.181 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) collect banned table[0]: recipient@myserver.com, tables: DEFAULT=>Amavis::Lookup::RE=ARRAY(0x2e1f188)
Sep 11 11:56:37.182 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) starting banned checks - traversing message structure tree
Sep 11 11:56:37.182 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) check_for_banned (p001) text/plain,.asc
Sep 11 11:56:37.182 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) doing banned check for recipient@myserver.com on text/plain,.asc
Sep 11 11:56:37.183 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_re(["text/plain",".asc"]), no matches
Sep 11 11:56:37.183 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [check_bann:recipient@myserver.com] => undef, ["text/plain",".asc"] does not match
Sep 11 11:56:37.183 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [banned_namepath_re] => undef, "P=p001\tL=1\tM=text/plain\tT=asc" does not match
Sep 11 11:56:37.183 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) p.path recipient@myserver.com: "P=p001,L=1,M=text/plain,T=asc"
Sep 11 11:56:37.184 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) banned check: any=0, all=N (1)
Sep 11 11:56:37.184 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_re("MAIL"), no matches
Sep 11 11:56:37.184 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [keep_decoded_original] => undef, "MAIL" does not match
Sep 11 11:56:37.185 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Calling virus scanners, 1 files to scan in /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts
Sep 11 11:56:37.185 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) invoking av-scanner ClamAV-clamd
Sep 11 11:56:37.185 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) ask_daemon: proto=DFLT, spawn=0, (ClamAV-clamd) /var/run/clamav/clamd.ctl
Sep 11 11:56:37.185 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) run_av (ClamAV-clamd): query template(1,0): CONTSCAN {}\n
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline run_av_pre - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer run_av_pre: timer 288, was 288, deadline in 479.9 s
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline run_av_scan - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer run_av_scan: timer 288, was 288, deadline in 479.9 s
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) run_av Using (ClamAV-clamd): (code) CONTSCAN /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts\n
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline ask_daemon_internal_connect_pre - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline ask_daemon_internal_connect - deadline in 479.9 s, set to 10.000 s
Sep 11 11:56:37.186 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer ask_daemon_internal_connect: timer 10, was 288, deadline in 479.9 s
Sep 11 11:56:37.187 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) ClamAV-clamd: Connecting to socket  /var/run/clamav/clamd.ctl
Sep 11 11:56:37.187 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) new socket by IO::Socket::UNIX to /var/run/clamav/clamd.ctl, timeout set to 10
Sep 11 11:56:37.188 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) connected to /var/run/clamav/clamd.ctl successfully
Sep 11 11:56:37.188 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) ClamAV-clamd: Sending CONTSCAN /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts\n to socket /var/run/clamav/clamd.ctl
Sep 11 11:56:37.188 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop: needline=0, flush=1, wr=1, timeout=10
Sep 11 11:56:37.188 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop: sending 73 chars
Sep 11 11:56:37.188 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop sent 73> CONTSCAN /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts\n
Sep 11 11:56:37.189 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline ask_daemon_internal_scan - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.189 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer ask_daemon_internal_scan: timer 288, was 10, deadline in 479.9 s
Sep 11 11:56:37.189 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop: needline=0, flush=0, wr=0, timeout=287.997
Sep 11 11:56:37.189 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop: receiving
Sep 11 11:56:37.189 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop read 68 chars< /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts: OK\n
Sep 11 11:56:37.189 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop: needline=0, flush=0, wr=0, timeout=287.997
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop: receiving
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rw_loop read: got eof
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline ask_daemon_internal - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer ask_daemon_internal: timer 288, was 288, deadline in 479.9 s
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline run_av_3 - deadline in 479.9 s, set to 288.000 s
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer run_av_3: timer 288, was 288, deadline in 479.9 s
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) run_av (ClamAV-clamd) result: /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts: OK\n
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) run_av (ClamAV-clamd): CLEAN
Sep 11 11:56:37.190 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) run_av (ClamAV-clamd) result: clean
Sep 11 11:56:37.191 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) wbl: checking sender <out@gmail.com>, <root@mail.gmail.com>
Sep 11 11:56:37.191 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [blacklist_recip<recipient@myserver.com>] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.192 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [blacklist_sender<out@gmail.com>,blacklist_sender] => undef, "out@gmail.com" does not match
Sep 11 11:56:37.192 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [whitelist_recip<recipient@myserver.com>] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.192 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [whitelist_sender<out@gmail.com>,whitelist_sender] => undef, "out@gmail.com" does not match
Sep 11 11:56:37.192 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) query_keys: recipient@myserver.com, f@, myserver.com, .myserver.com, .com, .
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_hash(recipient@myserver.com) matches keys: "."=>ARRAY(0x2d90318)
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [score_recip<recipient@myserver.com>,score_sender], 1 matches for "recipient@myserver.com", results: "."=>[Amavis::Lookup::RE=ARRAY(0x2d90600),{}]
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_re("out@gmail.com"), no matches
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [score_sender<out@gmail.com>] => undef, "out@gmail.com" does not match
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [blacklist_recip<recipient@myserver.com>] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [blacklist_sender<root@mail.gmail.com>,blacklist_sender] => undef, "root@mail.gmail.com" does not match
Sep 11 11:56:37.193 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [whitelist_recip<recipient@myserver.com>] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [whitelist_sender<root@mail.gmail.com>,whitelist_sender] => undef, "root@mail.gmail.com" does not match
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) query_keys: cached recipient@myserver.com
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_hash(recipient@myserver.com) matches keys: "."=>ARRAY(0x2d90318)
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [score_recip<recipient@myserver.com>,score_sender], 1 matches for "recipient@myserver.com", results: "."=>[Amavis::Lookup::RE=ARRAY(0x2d90600),{}]
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup_re("root@mail.gmail.com"), no matches
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [score_sender<root@mail.gmail.com>] => undef, "root@mail.gmail.com" does not match
Sep 11 11:56:37.194 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) SpamControl: calling spam scanner SpamAssassin
Sep 11 11:56:37.195 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline spam_scan_sa_pre - deadline in 479.9 s, set to 476.000 s
Sep 11 11:56:37.195 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer spam_scan_sa_pre: timer 476, was 288, deadline in 479.9 s
Sep 11 11:56:37.195 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) SA user config: "", username: "amavis", 0, (0)recipient@myserver.com
Sep 11 11:56:37.196 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) calling SA parse (0), SA vers 3.4.0, 3.004000, data as STRING_REF, recips_ind [0], user: "amavis"
Sep 11 11:56:37.197 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline SA check - deadline in 479.9 s, set to 475.000 s
Sep 11 11:56:37.200 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) CALLING SA check (0)
Sep 11 11:56:38.498 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) DONE SA check (0)
Sep 11 11:56:38.501 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline spam_scan_sa - deadline in 478.6 s, set to 288.000 s
Sep 11 11:56:38.501 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer spam_scan_sa: timer 288, was 475, deadline in 478.6 s
Sep 11 11:56:38.502 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) spam_scan: score=1000 autolearn=no autolearn_force=no tests=[GTUBE=1000] recips=0
Sep 11 11:56:38.502 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline spam_scan - deadline in 478.6 s, set to 288.000 s
Sep 11 11:56:38.502 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer spam_scan: timer 288, was 288, deadline in 478.6 s
Sep 11 11:56:38.502 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="2"
Sep 11 11:56:38.502 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_tag_level] => true,  "recipient@myserver.com" matches, result="2", matching_key="(constant:2)"
Sep 11 11:56:38.502 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="6.31"
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_tag2_level] => true,  "recipient@myserver.com" matches, result="6.31", matching_key="(constant:6.31)"
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_tag3_level] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="6.31"
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_kill_level] => true,  "recipient@myserver.com" matches, result="6.31", matching_key="(constant:6.31)"
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [Lovers2,spam_lovers] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) blocking contents category is (6) for recipient@myserver.com, final_destiny -2
Sep 11 11:56:38.503 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) final_destiny -2, recip recipient@myserver.com
Sep 11 11:56:38.505 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) blocking ccat=6, SMTP response: 554 5.7.0 Bounce, id=11707-01 - spam
Sep 11 11:56:38.505 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) do_notify_and_quar: ccat=Spam (6,0) ("6":Spam, "5":Spammy, "1,1":CleanTag, "1":Clean, "0":CatchAll) ccat_block=(6), qar_mth=
Sep 11 11:56:38.505 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="spam-quarantine"
Sep 11 11:56:38.505 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_quarantine_to] => true,  "recipient@myserver.com" matches, result="spam-quarantine", matching_key="(constant:spam-quarantine)"
Sep 11 11:56:38.506 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_quarantine_cutoff_level] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:38.506 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_admin] => undef, "recipient@myserver.com" does not match
Sep 11 11:56:38.506 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_quarantine_bysender_to] => undef, "out@gmail.com" does not match
Sep 11 11:56:38.506 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="2"
Sep 11 11:56:38.506 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_tag_level] => true,  "recipient@myserver.com" matches, result="2", matching_key="(constant:2)"
Sep 11 11:56:38.506 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="6.31"
Sep 11 11:56:38.507 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_tag2_level] => true,  "recipient@myserver.com" matches, result="6.31", matching_key="(constant:6.31)"
Sep 11 11:56:38.507 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="6.31"
Sep 11 11:56:38.507 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_kill_level] => true,  "recipient@myserver.com" matches, result="6.31", matching_key="(constant:6.31)"
Sep 11 11:56:38.507 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header_edits_for_quar: <out@gmail.com> -> <recipient@myserver.com>, Yes, score=1000 tag=2 tag2=6.31 kill=6.31 tests=[GTUBE=1000] autolearn=no autolearn_force=no
Sep 11 11:56:38.507 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Spam-Flag: YES
Sep 11 11:56:38.507 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Spam-Flag: YES\n
Sep 11 11:56:38.508 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Spam-Score: 1000
Sep 11 11:56:38.508 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Spam-Score: 1000\n
Sep 11 11:56:38.508 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Spam-Level: ****************************************************************
Sep 11 11:56:38.508 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Spam-Level: ****************************************************************\n
Sep 11 11:56:38.508 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Spam-Status: Yes,\n score=1000\n tag=2\n tag2=6.31\n kill=6.31\n tests=[GTUBE=1000]\n autolearn=no autolearn_force=no
Sep 11 11:56:38.509 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Spam-Status: Yes, score=1000 tag=2 tag2=6.31 kill=6.31 tests=[GTUBE=1000]\n\tautolearn=no autolearn_force=no\n
Sep 11 11:56:38.509 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) quar: scanner provided a header field X-Spam-Checker-Version, inhibited by %allowed_added_header_fields
Sep 11 11:56:38.509 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) quar: scanner provided a header field X-Spam-Flag, but we preferred our own
Sep 11 11:56:38.509 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) quar: scanner provided a header field X-Spam-Level, but we preferred our own
Sep 11 11:56:38.509 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) quar: scanner provided a header field X-Spam-Status, but we preferred our own
Sep 11 11:56:38.509 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) do_notify_and_quarantine: quarantine spam-quarantine
Sep 11 11:56:38.511 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Quarantine-ID: <ja7aIXNm4vr5>
Sep 11 11:56:38.511 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Quarantine-ID: <ja7aIXNm4vr5>\n
Sep 11 11:56:38.511 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Envelope-To-Blocked: <recipient@myserver.com>
Sep 11 11:56:38.511 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Envelope-To-Blocked: <recipient@myserver.com>\n
Sep 11 11:56:38.511 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): X-Envelope-To: <recipient@myserver.com>
Sep 11 11:56:38.511 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: X-Envelope-To: <recipient@myserver.com>\n
Sep 11 11:56:38.512 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): Received: from mail.myserver.com ([127.0.0.1])\n by localhost (mail.myserver.com [127.0.0.1]) (amavisd-new, port 10024)\n with LMTP\n id ja7aIXNm4vr5\n for <recipient@myserver.com>;\n Fri, 11 Sep 2015 11:56:37 +0000 (UTC)
Sep 11 11:56:38.512 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: Received: from mail.myserver.com ([127.0.0.1])\n\tby localhost (mail.myserver.com [127.0.0.1]) (amavisd-new, port 10024)\n\twith LMTP id ja7aIXNm4vr5 for <recipient@myserver.com>;\n\tFri, 11 Sep 2015 11:56:37 +0000 (UTC)\n
Sep 11 11:56:38.513 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) DO_QUARANTINE, local:spam-%m.gz, <out@gmail.com> -> <spam-quarantine>
Sep 11 11:56:38.513 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) delivering to local:spam-%m.gz, SEND via LOCAL: <out@gmail.com> -> <spam-quarantine>
Sep 11 11:56:38.514 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) local delivery: <out@gmail.com> -> spam-quarantine, mbx=/var/lib/amavis/virusmails/j/spam-ja7aIXNm4vr5.gz
Sep 11 11:56:38.517 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): Delivered-To: spam-quarantine
Sep 11 11:56:38.518 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: Delivered-To: spam-quarantine\n
Sep 11 11:56:38.518 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header encoded (all-ASCII): Return-Path: <out@gmail.com>
Sep 11 11:56:38.518 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) header: Return-Path: <out@gmail.com>\n
Sep 11 11:56:38.518 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) write_header: 1, Amavis::IO::Zlib=HASH(0x7e32138)
Sep 11 11:56:38.520 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) one_response_for_all, per_recip_capable: N, suppressed: N
Sep 11 11:56:38.520 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) one_response_for_all <out@gmail.com>: success, r=0,b=0,d=0, ndn_needed=0, '250 2.6.0 Ok, delivered to /var/lib/amavis/virusmails/j/spam-ja7aIXNm4vr5.gz, id=11707-01'
Sep 11 11:56:38.521 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) quar_types: Z, quar_to: /var/lib/amavis/virusmails/j/spam-ja7aIXNm4vr5.gz
Sep 11 11:56:38.521 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) DO_QUARANTINE done
Sep 11 11:56:38.521 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) skip admin notification, no administrators
Sep 11 11:56:38.521 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) do_notify_and_quarantine - done
Sep 11 11:56:38.521 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (opaque) matches, result="smtp:[127.0.0.1]:10025"
Sep 11 11:56:38.522 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [forward_method] => true,  "recipient@myserver.com" matches, result="smtp:[127.0.0.1]:10025", matching_key="(opaque:smtp:[127.0.0.1]:10025)"
Sep 11 11:56:38.522 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) delivery method is 1, recips: recipient@myserver.com
Sep 11 11:56:38.522 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline quar+notif - deadline in 478.5 s, set to 288.000 s
Sep 11 11:56:38.522 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer quar+notif: timer 288, was 288, deadline in 478.5 s
Sep 11 11:56:38.523 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) DSN: sender NOT credible, SA: 1000.000, <out@gmail.com>
Sep 11 11:56:38.523 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup: (scalar) matches, result="10"
Sep 11 11:56:38.523 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) lookup [spam_dsn_cutoff_level_bysender] => true,  "out@gmail.com" matches, result="10", matching_key="(constant:10)"
Sep 11 11:56:38.523 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) dsn: . 554 Spam <out@gmail.com> -> <recipient@myserver.com>: on_succ=0, on_dly=1, on_fail=1, never=0, warn_sender=, DSN_passed_on=, destiny=-2, mta_resp: "554 5.7.0 Bounce, id=11707-01 - spam"
Sep 11 11:56:38.524 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) DSN: FILTER 554 Spam, spam level 1000.000 exceeds cutoff 10, <out@gmail.com> -> <recipient@myserver.com>
Sep 11 11:56:38.524 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) delivery_status_notification: notif 0 bytes, suppressed: yes
Sep 11 11:56:38.524 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) one_response_for_all, per_recip_capable: Y, suppressed: Y
Sep 11 11:56:38.524 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) one_response_for_all <out@gmail.com>: mixed, r=0,b=1,d=0, ndn_needed=1, '250 2.5.0 Ok, id=11707-01, DISCARD(bounce.suppressed)'
Sep 11 11:56:38.525 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) notif=N, suppressed=1, ndn_needed=1, exit=99, 250 2.5.0 Ok, id=11707-01, DISCARD(bounce.suppressed)
Sep 11 11:56:38.525 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline delivery-notification - deadline in 478.5 s, set to 288.000 s
Sep 11 11:56:38.525 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer delivery-notification: timer 288, was 288, deadline in 478.5 s
Sep 11 11:56:38.525 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) status counters: InMsgsStatus{NoBounce,NoBounceOpenRelay}
Sep 11 11:56:38.525 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline snmp-counters - deadline in 478.5 s, set to 288.000 s
Sep 11 11:56:38.525 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer snmp-counters: timer 288, was 288, deadline in 478.5 s
Sep 11 11:56:38.526 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) orcpt_encode rfc822, recipient@myserver.com, smtputf8
Sep 11 11:56:38.532 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) oldest_public_ip_addr_from_received: 139.162.196.38
Sep 11 11:56:38.534 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) Blocked SPAM {NoBounceOpenRelay,Quarantined}, [139.162.196.38]:38301 [139.162.196.38] <out@gmail.com> -> <recipient@myserver.com>, quarantine: j/spam-ja7aIXNm4vr5.gz, Queue-ID: EA60D7926B8, Message-ID: <20150911115635.GA2675@mail.gmail.com>, mail_id: ja7aIXNm4vr5, Hits: 1000, size: 696, 1529 ms
Sep 11 11:56:38.534 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline main_log_entry - deadline in 478.5 s, set to 288.000 s
Sep 11 11:56:38.534 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer main_log_entry: timer 288, was 288, deadline in 478.5 s
Sep 11 11:56:38.534 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) TIMING-SA total 1303 ms - parse: 2.2 (0.2%), extract_message_metadata: 6 (0.5%), get_uri_detail_list: 0.20 (0.0%), tests_pri_-1000: 4.6 (0.4%), tests_pri_-950: 1.51 (0.1%), tests_pri_-900: 1.76 (0.1%), tests_pri_-400: 1.03 (0.1%), tests_pri_0: 1248 (95.8%), check_dkim_signature: 1.34 (0.1%), check_dkim_adsp: 99 (7.6%), check_spf: 1104 (84.8%), poll_dns_idle: 1084 (83.2%), check_pyzor: 0.24 (0.0%), tests_pri_500: 3.0 (0.2%), get_report: 0.39 (0.0%)
Sep 11 11:56:38.535 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) updating snmp variables in BDB
Sep 11 11:56:38.537 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline check done - deadline in 478.5 s, set to 288.000 s
Sep 11 11:56:38.537 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer check done: timer 288, was 288, deadline in 478.5 s
Sep 11 11:56:38.537 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP response for <recipient@myserver.com>: "250 2.5.0 Ok <recipient@myserver.com>, DSN suppressed (554 5.7.0 Bounce, id=11707-01 - spam)"
Sep 11 11:56:38.537 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 250 2.5.0 Ok <recipient@myserver.com>, DSN suppressed (554 5.7.0 Bounce, id=11707-01 - spam)
Sep 11 11:56:38.537 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:38.537 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) TempDir::strip: /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV
Sep 11 11:56:38.538 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) rmdir_recursively: /var/lib/amavis/tmp/amavis-20150911T115637-11707-0I1ZrvUV/parts, excl=1
Sep 11 11:56:38.539 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) size: 696, TIMING [total 1534 ms] - SMTP greeting: 14 (1%)1, SMTP LHLO: 4.8 (0%)1, SMTP pre-MAIL: 4.9 (0%)2, mkdir tempdir: 1.7 (0%)2, create email.txt: 0.5 (0%)2, SMTP pre-DATA-flush: 6 (0%)2, SMTP DATA: 31 (2%)4, check_init: 1.3 (0%)4, digest_hdr: 1.3 (0%)4, digest_body: 1.1 (0%)4, collect_info: 4.1 (0%)5, mkdir parts: 2.6 (0%)5, mime_decode: 18 (1%)6, get-file-type1: 83 (5%)11, parts_decode: 0.5 (0%)11, check_header: 1.3 (0%)12, AV-scan-1: 10 (1%)12, spam-wb-list: 3.6 (0%)12, SA msg read: 1.0 (0%)12, SA parse: 5 (0%)13, SA check: 1298 (85%)97, decide_mail_destiny: 7 (0%)98, notif-quar: 1.1 (0%)98, quar-hdrs: 3.4 (0%)98, stat-mbx: 4.6 (0%)98, open-mbx: 3.3 (0%)99, write-header: 1.4 (0%)99, save-to-local-mailbox: 1.2 (0%)99, prepare-dsn: 4.7 (0%)99, report: 3.2 (0%)99, main_log_entry: 6 (0%)100, update_snmp: 2.1 (0%)100, SMTP pre-response: 0.6 (0%)100, SMTP response: 0.6 (0%)100, unlink-1-files: 0.4 (0%)100, rundown: 1.0 (0%)100
Sep 11 11:56:38.539 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 6: was busy, 1504.8 ms, total idle 0.002 s, busy 1.533 s
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, 5: was idle, 0.2 ms, total idle 0.002 s, busy 1.533 s
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP< QUIT\r\n
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) get_deadline switch_to_my_time(rx SMTP QUIT) - deadline in 480.0 s, set to 288.000 s
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) prolong_timer switch_to_my_time(rx SMTP QUIT): timer 288, was 480, deadline in 480.0 s
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) LMTP> 221 2.0.0 [127.0.0.1] amavisd-new closing transmission channel
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) switch_to_client_time 480 s, smtp response sent
Sep 11 11:56:38.540 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) SMTP session over, timer stopped
Sep 11 11:56:38.544 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) exiting process_request
Sep 11 11:56:38.544 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) idle_proc, bye: was busy, 4.5 ms, total idle 0.002 s, busy 1.537 s
Sep 11 11:56:38.544 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) load: 100 %, total idle 0.002 s, busy 1.537 s
Sep 11 11:56:55.614 mail.myserver.com /usr/sbin/amavisd-new[11708]: child_goes_idle (child finishing)
Sep 11 11:56:55.614 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) child_goes_idle: disconnected none (child finishing)
Sep 11 11:56:55.614 mail.myserver.com /usr/sbin/amavisd-new[11708]: child_goes_idle: disconnected none (child finishing)
Sep 11 11:56:55.614 mail.myserver.com /usr/sbin/amavisd-new[11707]: (11707-01) SA rundown_child (0)
Sep 11 11:56:55.614 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: 2015/09/11-11:56:55 Server closing!
Sep 11 11:56:55.615 mail.myserver.com /usr/sbin/amavisd-new[11708]: SA rundown_child (0)
Sep 11 11:56:55.615 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Kill TERM pid 11707
Sep 11 11:56:55.615 mail.myserver.com /usr/sbin/amavisd-new[11699]: Net::Server: Kill TERM pid 11708
Sep 11 11:56:55.615 mail.myserver.com /usr/sbin/amavisd-new[11708]: child_goes_idle (child finishing)
Sep 11 11:56:55.616 mail.myserver.com /usr/sbin/amavisd-new[11708]: child_goes_idle: disconnected none (child finishing)
Sep 11 11:56:55.616 mail.myserver.com /usr/sbin/amavisd-new[11708]: SA rundown_child (0)
Sep 11 11:56:55.616 mail.myserver.com /usr/sbin/amavisd-new[11708]: SpamControl: rundown_child on SpamAssassin done
Sep 11 11:56:55.617 mail.myserver.com /usr/sbin/amavisd-new[11708]: child_finish_hook: invoking DESTROY methods
Sep 11 11:56:55.618 mail.myserver.com /usr/sbin/amavisd-new[11708]: Amavis::DB::SNMP DESTROY called
```

And my /etc/amavis/conf.d/20-debian_defaults: ```
$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)                                                                                                                                                      
$final_banned_destiny     = D_BOUNCE;   # D_REJECT when front-end MTA                                                                                                                                                                
$final_spam_destiny       = D_BOUNCE;                                                                                                                                                                                                
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)                                                                                                                                                            

```
So my expected behavior is: message marked as spam will be delivered into mailbox(and then I can configure sieve or something like that ).
Message is not delivered into mailbox as I expect. Where is the message lost? How can I configure it for deliver SPAM into mailbox? Thank you for all hints, I'll post whatever, I'm new to amavis/spamassassin. Thanks!

---

