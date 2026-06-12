---
title: "bacula 2.4.0 on ubunutu 6.06 ZLIB support"
date: 2008-06-14
forum: General Help
---

### Post by rmvg on 2008-06-14
Hello all i am tring to install bacula-fd 2.4.0 on my ubuntu 6.06.2 LTS server box. Mostly it works but i cannot get it to compile with ZLIB support. 

The version of bacula in the repositories is to old 1.36 and does not work with my 2.4.0 director.  I have searched high an low for a bacula 2 deb the works with 6.06 but have found nothing yet. If there is on i would be glad to us it instead of tring to make the source compile with ZLIB supporthere is the post as it appears on bacula mailing list   

Ok i installed zlib.a on my ubuntu  
 
I did a new configure of bacula and still get ZLIB = no at the end, even tried ./configure --ZLIB=yes --enable-client-only. thought maybe bacula could not find the zlib.a file so i symbolically linked it to /lib /usr/lib and it lives in /usr/local/lib i am triing really hard here but getting nowhere
 
what should i do???
- Hide quoted text -


 
On Sat, Jun 14, 2008 at 2:50 PM, RYAN vAN GINNEKEN <vanginnekenr@gmail.com> wrote:

forgot this 
 
c0mputerking@ubuntu:~/bacula-2.4.0$ ldd /sbin/bacula-fd
ldd: warning: you do not have execution permission for `/sbin/bacula-fd'
        linux-gate.so.1 =>  (0xffffe000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f1a000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7e44000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e22000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7e18000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ce9000)
        /lib/ld-linux.so.2 (0x80000000)



 
On Sat, Jun 14, 2008 at 2:39 PM, RYAN vAN GINNEKEN <vanginnekenr@gmail.com> wrote:

Thanks arno I think you are right here is the output of lld. Would i run 
 
./configure --enable-client-only --with-compression? how do i recompile with compression I am coming from Freebsd to ubuntu 6.06 LST and am still really new with this manual configure stuff I looked in the doc and could not find mention of the compression switch 
 
Thank you thus far and please help
 


 
On Sat, Jun 14, 2008 at 2:15 PM, Arno Lehmann <al@its-lehmann.de> wrote:

Hi,


14.06.2008 21:23, RYAN vAN GINNEKEN wrote:
> I have a bacula 2.2.6 on freebsd machine and have on several attempts
> tried to do a restore to 2.4.0 and get failures.  Are these version
> incompatable?? I might be able to upgrade the version on the freebsd
> machine but i am in recovery mode here and cannot afford to lose the
> data contain in bacula 2.2.6
>
> here are the errors
>
>
>
> *14-Jun 19:10 rescue-fd JobId 1175: Error: GZIP data stream not
> supported on this Client.


This looks like your client is compiled without suppression support.

the command 'ldd /path/to/bacula-fd' should tell you if libz is needed
by it. If it isn't, you will have to recompile the FD with compression
support.

Otherwise, I don't know what's wrong.

Arno


> 14-Jun: is an invalid command.
> 14-Jun 13:01 miako-sd JobId 1175: Reposition from (file:block)
> 3:138159139 to 3:1774098474
> 14-Jun 19:10 rescue-fd JobId 1175: Error: 8 non-supported data streams
> and 0 non-supported attrib streams ignored.
> 14-Jun 13:02 miako-dir JobId 1175: Error: Bacula miako-dir 2.2.6
> (10Nov07): 14-Jun-2008 13:01:59
>
> *14-Jun 13:01 miako-sd JobId 1175: Reposition from (file:block)
> 3:138159139 to 3:1774098474
> 14-Jun: is an invalid command.
> *14-Jun 19:10 rescue-fd JobId 1175: Error: 8 non-supported data streams
> and 0 non-supported attrib streams ignored.
> 14-Jun: is an invalid command.
> *14-Jun 13:02 miako-dir JobId 1175: Error: Bacula miako-dir 2.2.6
> (10Nov07): 14-Jun-2008 13:01:59
> 14-Jun: is an invalid command.
>
> THIS IS A DEBUG OF THE CLIENT
>
> yVolume
> rescue-fd: job.c:1736-0 >stored: read open session = DummyVolume 38
> 1213057385 0 0 0 0
> rescue-fd: job.c:1742-0 bfiled<stored: 3000 OK open ticket = 38
> rescue-fd: job.c:1747-0 bfiled: got Ticket=38
> rescue-fd: job.c:1830-0 send_bootstrap_file:
> /var/lib/bacula/rescue-fd.Restore-canmail.org.2008-06-14_13.00.26.2.bootstrap
> rescue-fd: job.c:1804-0 3000 OK bootstrap
> rescue-fd: job.c:1761-0 >stored: read data 38
> rescue-fd: job.c:1804-0 3000 OK data
> rescue-fd: jcr.c:603-0 OnEntry JobStatus=B set=R
> rescue-fd: jcr.c:623-0 OnExit JobStatus=R set=R
> rescue-fd: jcr.c:603-0 OnEntry JobStatus=R set=R
> rescue-fd: jcr.c:623-0 OnExit JobStatus=R set=R
> rescue-fd: bsock.c:618-0 set network buffer size=65536
> rescue-fd: bnet.c:667-0 who=client host=192.168.1.100

> <http://192.168.1.100> port=36387

> rescue-fd: jcr.c:603-0 OnEntry JobStatus=rescue-fd: jcr.c:623-0 OnExit
> JobStatus=C set=C
> rescue-fd: find.c:81-0 init_find_files ff=80a9d90
> rescue-fd: job.c:233-0 <dird: Hello Director miako-dir calling
> rescue-fd: job.c:249-0 Executing Hello command.
> rescue-fd: job.c:359-0 Calling Authenticate
> rescue-fd: watchdog.c:193-0 Registered watchdog 80a9fa8, interval 600
> one shot
> rescue-fd: btimers.c:179-0 Start bsock timer 80aa930 tid=b73fabb0 for
> 600 secs at 1213470621
> rescue-fd: cram-md5.c:73-0 send: auth cram-md5

> <825860972.1213470621@rescue-fd <mailto:825860972.1213470621@rescue-fd>>

> ssl=0
> rescue-fd: cram-md5.c:133-0 cram-get received: auth cram-md5
> <1469742137.1213448494@miako-dir

> <mailto:1469742137.1213448494@miako-dir>> ssl=0

> rescue-fd: cram-md5.c:152-0 sending resp to challenge:
> q4+v20p/FE+NR/UXg//hOB
> rescue-fd: btimers.c:193-0 Stop bsock timer 80aa930 tid=b73fabb0 at
> 1213470621.
> rescue-fd: watchdog.c:213-0 Unregistered watchdog 80a9fa8
> rescue-fd: job.c:363-0 OK Authenticate
> rescue-fd: job.c:233-0 <dird: JobId=0 Job=-Console-.2008-06-14_12.48.23
> SDid=0 SDtime=0 Authorization=dummy
> rescue-fd: job.c:249-0 Executing JobId= command.
> rescue-fd: job.c:457-0 JobId=0 Auth=dummy
> rescue-fd: job.c:233-0 <dird: statusrescue-fd: job.c:249-0 Executing
> status command.
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: status.c:143-0 Begin status jcr loop.
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: mem_pool.c:568-0 max_size=512
> rescue-fd: runscript.c:103-0 runscript: running all RUNSCRIPT object
> (ClientAfterJob) JobStatus=C
> rescue-fd: job.c:343-0 Calling term_find_files
> rescue-fd: job.c:346-0 Done with term_find_files
> rescue-fd: runscript.c:252-0 runscript: freeing all RUNSCRIPTS object
> rescue-fd: message.c:416-0 Close_msg jcr=80bb8b8
> rescue-fd: message.c:416-0 Close_msg jcr=0
> rescue-fd: message.c:428-0 ===Begin close msg resource at 80a85e0
> rescue-fd: message.c:512-0 Done walking message chain.
> rescue-fd: message.c:519-0 ===End close msg resource
> rescue-fd: mem_pool.c:377-0 garbage collect memory pool
> rescue-fd: job.c:348-0 Done with free_jcr
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426049 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=106 extract=0
> rescue-fd: attr.c:77-0 Attr: 426049 3 /home/c0mputerking/seagate/stlog.txt
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426049 type=3
> rescue-fd: attr.c:116-0 unpack_attr FI=426049 Type=3
> fname=/home/c0mputerking/seagate/stlog.txt attr=P0A G1YAO IGk B A A A OT
> BAA I BIQnQJ BG9YZY BHcbTo A A E lname= attrEx= ds=0
> rescue-fd: restore.c:333-0 File /home/c0mputerking/seagate/stlog.txt
> attrib=P0A G1YAO IGk B A A A OT BAA I BIQnQJ BG9YZY BHcbTo A A E
> attribsEx=
> rescue-fd: message.c:1083-0 Enter Jmsg type=4
> rescue-fd: message.c:609-0 Enter dispatch_msg type=4 msg=rescue-fd JobId
> 1175: Error: GZIP data stream not supported on this Client.
> rescue-fd: message.c:781-0 DIRECTOR for following msg: rescue-fd JobId
> 1175: Error: GZIP data stream not supported on this Client.
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426049 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=343 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426049 Stream=3, MD5
> digest.
> rescue-fd: restore.c:272-0 Got stream: MD5 digest len=16 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426050 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=108 extract=0
> rescue-fd: attr.c:77-0 Attr: 426050 3 /home/c0mputerking/seagate/sthelp.txt
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426050 type=3
> rescue-fd: attr.c:116-0 unpack_attr FI=426050 Type=3
> fname=/home/c0mputerking/seagate/sthelp.txt attr=P0A G1YAN IEk B A A A
> L+w BAA Bg BIQnQJ 7ny2h BHcbTo A A E lname= attrEx= ds=0
> rescue-fd: restore.c:333-0 File /home/c0mputerking/seagate/sthelp.txt
> attrib=P0A G1YAN IEk B A A A L+w BAA Bg BIQnQJ 7ny2h BHcbTo A A E
> attribsEx=
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426050 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=16451 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426050 Stream=3, MD5
> digest.
> rescue-fd: restore.c:272-0 Got stream: MD5 digest len=16 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426051 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=108 extract=0
> rescue-fd: attr.c:77-0 Attr: 426051 3 /home/c0mputerking/seagate/UcliEvt.log
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426051 type=3
> rescue-fd: attr.c:116-0 unpack_attr FI=426051 Type=3
> fname=/home/c0mputerking/seagate/UcliEvt.log attr=P0A G1YA0 IGk B A A A
> Ok BAA I BIQnQJ BHG+6S BHcbT1 A A E lname= attrEx= ds=0
> rescue-fd: restore.c:333-0 File /home/c0mputerking/seagate/UcliEvt.log
> attrib=P0A G1YA0 IGk B A A A Ok BAA I BIQnQJ BHG+6S BHcbT1 A A E
> attribsEx=
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426051 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=198 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426051 Stream=3, MD5
> digest.
> rescue-fd: restore.c:272-0 Got stream: MD5 digest len=16 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426052 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=100 extract=0
> rescue-fd: attr.c:77-0 Attr: 426052 3 /home/c0mputerking/seagate/st
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426052 type=3
> rescue-fd: attr.c:116-0 unpack_attr FI=426052 Type=3
> fname=/home/c0mputerking/seagate/st attr=P0A G1YAM IHt B A A A r+1 BAA
> Fo BIQnQJ 7ny2d BHcbTo A A E lname= attrEx= ds=0
> rescue-fd: restore.c:333-0 File /home/c0mputerking/seagate/st
> attrib=P0A G1YAM IHt B A A A r+1 BAA Fo BIQnQJ 7ny2d BHcbTo A A E
> attribsEx=
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426052 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=22967 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426052 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=23616 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426052 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=16970 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426052 Stream=3, MD5
> digest.
> rescue-fd: restore.c:272-0 Got stream: MD5 digest len=16 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426053 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=108 extract=0
> rescue-fd: attr.c:77-0 Attr: 426053 3 /home/c0mputerking/seagate/UcliErr.log
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426053 type=3
> rescue-fd: attr.c:116-0 unpack_attr FI=426053 Type=3
> fname=/home/c0mputerking/seagate/UcliErr.log attr=P0A G1YBK IGk B A A A
> W4 BAA I BIQnQJ BHG+6T BHcbT1 A A E lname= attrEx= ds=0
> rescue-fd: restore.c:333-0 File /home/c0mputerking/seagate/UcliErr.log
> attrib=P0A G1YBK IGk B A A A W4 BAA I BIQnQJ BHG+6T BHcbT1 A A E
> attribsEx=
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426053 Stream=4, GZIP
> data.
> rescue-fd: restore.c:272-0 Got stream: GZIP data len=226 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426053 Stream=3, MD5
> digest.
> rescue-fd: restore.c:272-0 Got stream: MD5 digest len=16 extract=0
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426054 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=98 extract=0
> rescue-fd: attr.c:77-0 Attr: 426054 5 /home/c0mputerking/seagate/
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426054 type=5
> rescue-fd: attr.c:116-0 unpack_attr FI=426054 Type=5
> fname=/home/c0mputerking/seagate/ attr=P0A G1YAQ EHt C A A A BAA BAA I
> BIQnQJ BHcbT1 BHcbT1 A A E lname= attrEx= ds=0
> rescue-fd: restore.c:333-0 File /home/c0mputerking/seagate/
> attrib=P0A G1YAQ EHt C A A A BAA BAA I BIQnQJ BHcbT1 BHcbT1 A A E
> attribsEx=
> rescue-fd: restore.c:259-0 Got hdr: Files=0 FilInx=426119 Stream=1, Unix
> attributes.
> rescue-fd: restore.c:272-0 Got stream: Unix attributes len=92 extract=0
> rescue-fd: attr.c:77-0 Attr: 426119 5 /home/c0mputerking/
> rescue-fd: attr.c:83-0 Got Attr: FilInx=426119 type=5
> rescue-fd: attr.c:116-0 unpack_attr FI=426119 Type=5

---

