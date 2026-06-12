---
title: "Accessing Usenet"
date: 2012-12-26
forum: General Help
---

### Post by Robbyx on 2012-12-26
I have just installed Sabnzbdplus. When I load it via terminal I get a lot of error messages, but do not get the binary file:

```
robins@robins-EP35-DS3L:~$ sabnzbdplus
2012-12-26 21:33:37,597::INFO::[sabnzbdplus:1244] --------------------------------
2012-12-26 21:33:37,598::INFO::[sabnzbdplus:1245] sabnzbdplus-0.7.7 (rev=a82df9bf2e86c1d902145d2101c19401d8a589c3)
2012-12-26 21:33:37,598::INFO::[sabnzbdplus:1257] Platform = posix
2012-12-26 21:33:37,598::INFO::[sabnzbdplus:1258] Python-version = 2.7.3 (default, Aug  1 2012, 05:16:07) 
[GCC 4.6.3]
2012-12-26 21:33:37,598::INFO::[sabnzbdplus:1259] Arguments = /usr/bin/sabnzbdplus
2012-12-26 21:33:37,598::INFO::[sabnzbdplus:1272] Read INI file /home/robins/.sabnzbd/sabnzbd.ini
2012-12-26 21:33:37,599::INFO::[__init__:921] Loading data for bookmarks.sab from /home/robins/.sabnzbd/admin/bookmarks.sab
2012-12-26 21:33:37,600::INFO::[__init__:921] Loading data for rss_data.sab from /home/robins/.sabnzbd/admin/rss_data.sab
2012-12-26 21:33:37,600::INFO::[__init__:921] Loading data for totals9.sab from /home/robins/.sabnzbd/admin/totals9.sab
2012-12-26 21:33:37,600::INFO::[__init__:924] /home/robins/.sabnzbd/admin/totals9.sab missing, trying old cache
2012-12-26 21:33:37,600::INFO::[__init__:927] /home/robins/.sabnzbd/cache/totals9.sab missing
2012-12-26 21:33:38,147::INFO::[postproc:90] Loading postproc queue
2012-12-26 21:33:38,147::INFO::[__init__:921] Loading data for postproc1.sab from /home/robins/.sabnzbd/admin/postproc1.sab
2012-12-26 21:33:38,148::INFO::[__init__:921] Loading data for queue9.sab from /home/robins/.sabnzbd/admin/queue9.sab
2012-12-26 21:33:38,176::INFO::[__init__:921] Loading data for watched_data.sab from /home/robins/.sabnzbd/admin/watched_data.sab
2012-12-26 21:33:38,177::INFO::[downloader:208] Resuming
2012-12-26 21:33:38,177::INFO::[__init__:323] All processes started
2012-12-26 21:33:38,177::INFO::[sabnzbdplus:335] Web dir is /usr/share/sabnzbdplus/interfaces/Plush
2012-12-26 21:33:38,177::INFO::[sabnzbdplus:335] Web dir is /usr/share/sabnzbdplus/interfaces/Config
2012-12-26 21:33:38,182::INFO::[sabnzbdplus:451] _yenc module... found!
2012-12-26 21:33:38,182::INFO::[sabnzbdplus:459] par2 binary... found (/usr/bin/par2)
2012-12-26 21:33:38,182::INFO::[sabnzbdplus:467] unrar binary... found (/usr/bin/unrar)
2012-12-26 21:33:38,182::INFO::[sabnzbdplus:472] unzip binary... found (/usr/bin/unzip)
2012-12-26 21:33:38,182::INFO::[sabnzbdplus:478] nice binary... found (/usr/bin/nice)
2012-12-26 21:33:38,183::INFO::[sabnzbdplus:482] ionice binary... found (/usr/bin/ionice)
2012-12-26 21:33:38,183::INFO::[sabnzbdplus:487] pyOpenSSL... found (True)
2012-12-26 21:33:38,184::INFO::[sabnzbdplus:1471] Starting web-interface on 127.0.0.1:9090
2012-12-26 21:33:38,184::INFO::[_cplogging:55] [26/Dec/2012:21:33:38] ENGINE Bus STARTING
2012-12-26 21:33:38,186::INFO::[_cplogging:55] [26/Dec/2012:21:33:38] ENGINE Started monitor thread '_TimeoutMonitor'.
2012-12-26 21:33:38,287::INFO::[_cplogging:55] [26/Dec/2012:21:33:38] ENGINE Serving on 127.0.0.1:8080
2012-12-26 21:33:38,388::INFO::[_cplogging:55] [26/Dec/2012:21:33:38] ENGINE Serving on 127.0.0.1:9090
2012-12-26 21:33:38,389::INFO::[_cplogging:55] [26/Dec/2012:21:33:38] ENGINE Bus STARTED
2012-12-26 21:33:38,389::INFO::[panic:247] Lauching browser with https://localhost:9090/sabnzbd
2012-12-26 21:33:38,909::INFO::[growler:267] Send to NotifyOSD: SABnzbd@robins-ep35-ds3l / SABnzbd 0.7.7 started
2012-12-26 21:33:38,954::INFO::[sabnzbdplus:1540] Starting sabnzbdplus-0.7.7
2012-12-26 21:33:38,991::INFO::[urlgrabber:77] URLGrabber starting up
2012-12-26 21:33:38,979::INFO::[dirscanner:265] Dirscanner starting up
2012-12-26 21:33:39,993::INFO::[downloader:375] 1@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:39,993::ERROR::[downloader:380] Failed to initialize 1@newszilla6.xs4all.nl:119
2012-12-26 21:33:39,993::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:39,994::INFO::[downloader:640] Thread 1@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:39,995::INFO::[downloader:375] 2@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:39,995::ERROR::[downloader:380] Failed to initialize 2@newszilla6.xs4all.nl:119
2012-12-26 21:33:39,995::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:39,996::INFO::[downloader:640] Thread 2@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:39,996::INFO::[downloader:375] 3@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:39,996::ERROR::[downloader:380] Failed to initialize 3@newszilla6.xs4all.nl:119
2012-12-26 21:33:39,996::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:39,997::INFO::[downloader:640] Thread 3@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:39,997::INFO::[downloader:375] 4@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:39,997::ERROR::[downloader:380] Failed to initialize 4@newszilla6.xs4all.nl:119
2012-12-26 21:33:39,998::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:39,998::INFO::[downloader:640] Thread 4@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:39,999::INFO::[decoder:218] <Article: article=0004HW.CCDC47020257E3B4B06169DF@news.giganews.com, bytes=58009, partnum=1, art_id=None> => missing from all servers, discarding
2012-12-26 21:33:40,043::INFO::[downloader:375] 5@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,043::ERROR::[downloader:380] Failed to initialize 5@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,043::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,043::INFO::[downloader:640] Thread 5@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,043::INFO::[downloader:375] 6@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,043::ERROR::[downloader:380] Failed to initialize 6@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,044::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,044::INFO::[downloader:640] Thread 6@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,044::INFO::[downloader:375] 7@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,044::ERROR::[downloader:380] Failed to initialize 7@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,044::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,044::INFO::[downloader:640] Thread 7@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,045::INFO::[downloader:375] 8@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,045::ERROR::[downloader:380] Failed to initialize 8@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,045::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,045::INFO::[downloader:640] Thread 8@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,045::INFO::[downloader:375] 9@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,045::ERROR::[downloader:380] Failed to initialize 9@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,045::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,046::INFO::[downloader:640] Thread 9@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,046::INFO::[downloader:375] 10@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,046::ERROR::[downloader:380] Failed to initialize 10@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,046::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,046::INFO::[downloader:640] Thread 10@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,047::INFO::[downloader:375] 11@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,047::ERROR::[downloader:380] Failed to initialize 11@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,047::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,047::INFO::[downloader:640] Thread 11@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,047::INFO::[downloader:375] 12@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,047::ERROR::[downloader:380] Failed to initialize 12@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,047::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,048::INFO::[downloader:640] Thread 12@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,048::INFO::[downloader:375] 13@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,048::ERROR::[downloader:380] Failed to initialize 13@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,048::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,049::INFO::[downloader:640] Thread 13@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,049::INFO::[downloader:375] 14@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,049::ERROR::[downloader:380] Failed to initialize 14@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,049::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,049::INFO::[downloader:640] Thread 14@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,050::INFO::[downloader:375] 15@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,050::ERROR::[downloader:380] Failed to initialize 15@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,050::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,050::INFO::[downloader:640] Thread 15@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,050::INFO::[downloader:375] 16@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,050::ERROR::[downloader:380] Failed to initialize 16@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,051::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,051::INFO::[downloader:640] Thread 16@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,051::INFO::[downloader:375] 17@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,049::INFO::[decoder:218] <Article: article=0005HW.CCDC47020257E3DAB06169DF@news.giganews.com, bytes=55431, partnum=1, art_id=None> => missing from all servers, discarding
2012-12-26 21:33:40,051::ERROR::[downloader:380] Failed to initialize 17@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,051::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,052::INFO::[downloader:640] Thread 17@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,062::INFO::[downloader:375] 18@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,063::INFO::[decoder:218] <Article: article=0006HW.CCDC47030257E3F2B06169DF@news.giganews.com, bytes=48899, partnum=1, art_id=None> => missing from all servers, discarding
2012-12-26 21:33:40,062::ERROR::[downloader:380] Failed to initialize 18@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,064::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,064::INFO::[downloader:640] Thread 18@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,074::INFO::[downloader:375] 19@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,074::ERROR::[downloader:380] Failed to initialize 19@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,074::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,074::INFO::[downloader:640] Thread 19@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,074::INFO::[downloader:375] 20@newszilla6.xs4all.nl:119: Initiating connection
2012-12-26 21:33:40,075::INFO::[decoder:218] <Article: article=0007HW.CCDC47030257E413B06169DF@news.giganews.com, bytes=48319, partnum=1, art_id=None> => missing from all servers, discarding
2012-12-26 21:33:40,075::ERROR::[downloader:380] Failed to initialize 20@newszilla6.xs4all.nl:119
2012-12-26 21:33:40,075::INFO::[downloader:381] Traceback: 
Traceback (most recent call last):
  File "/usr/share/sabnzbdplus/sabnzbd/downloader.py", line 376, in run
    nw.init_connect(self.write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 263, in init_connect
    self.server.username, self.server.password, self.blocking, write_fds)
  File "/usr/share/sabnzbdplus/sabnzbd/newswrapper.py", line 165, in __init__
    raise socket.error(errno.EADDRNOTAVAIL, "Address not available - Check for internet or DNS problems")
error: [Errno 99] Address not available - Check for internet or DNS problems
2012-12-26 21:33:40,075::INFO::[downloader:640] Thread 20@newszilla6.xs4all.nl:119: failed to initialize
2012-12-26 21:33:40,086::INFO::[decoder:218] <Article: article=0008HW.CCDC47050257E460B06169DF@news.giganews.com, bytes=50975, partnum=1, art_id=None> => missing from all servers, discarding
  

```

All the above is before I even upload the nzb file for the download.

When I look at the web page in Firefox for the usenet access page I get an error message:

*Firefox can't establish a connection to the server at localhost:9090.*

What do the error messages suggest I have ommitted to do in the set up?

Robin

---

### Post by windscape on 2012-12-26
Hi,

The "Check for internet or DNS problems" error in your output indicates that the software could not connect to your configured news server, newszilla6.xs4all.nl on the configured port, 119. Is that the correct news server and port to use? Can you ping the news server? Try configuring the software to use a different news server.

---

### Post by Robbyx on 2012-12-26
> **windscape said:**
> Hi,

The "Check for internet or DNS problems" error in your output indicates that the software could not connect to your configured news server, newszilla6.xs4all.nl on the configured port, 119. Is that the correct news server and port to use? Can you ping the news server? Try configuring the software to use a different news server.

Can you please suggest where I make the changes to the ports?

In Sabnzbd general tab the  sabnzb web server shows the host is localhost and the port is 8080.

In its https support settings the port is 9090.

There is another screen for servers: There newszilla6.xs4all.nl is enabled and the port is 119. I clicked  the test server button and the message was:
[I]
Server quit during login sequence[/I]

Putting newszilla6.xs4all.nl into the FF address bar  produces a server not found error message. Does that mean newszilla6.xs4all.nl is down? How do I know what port to put into the server settings.

I have just found that the server is down, but I would appreciate some comments on my questions because I am not really sure how to set up the ports. 


Robin

---

### Post by dcstar on 2012-12-28
> **Robbyx said:**
> 
..........
**I have just found that the server is down**, but I would appreciate some comments on my questions because I am not really sure how to set up the ports. 


Different problem, mark this thread as Solved and start a new one.

---

