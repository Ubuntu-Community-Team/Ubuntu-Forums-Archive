---
title: "Package Manager"
date: 2014-08-12
forum: General Help
---

### Post by sagent3000 on 2014-08-12
I am having a problem and reached a point from which i dont know what to do next
i was getting this error 
> Unable to get exclusive lock.  This usually means that another package management application like apt-get or aptitude is already running. Please close that application first. 

so i searched forums and found where people had the same problem and used 
> rm /var/lib/dpkg/lock   
i ran that and then tried apt-get upgrade and got the errorE: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

i then ran that and get 
> Setting up nautilus-dropbox (0.7.1-2) ...


Dropbox is the easiest way to share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)


Downloading Dropbox... 100% 

and it just sits there.  i started this at 5pm and let it run thinking it was just an install but now at 5am it still stuck there i can type and hit enter and nothing happens.  i have rebooted several times and exited out of dropbox as well.  any suggestions?

---

### Post by ian-weisser on 2014-08-12
It hung for me, too.

Run the 'sudo dpkg --configure nautilus-dropbox' command again.
When it works properly, install only takes a minute or so after download completes.
Once it reaches 100%, give it a couple minutes to be sure it's really hung, then CTRL+C. You don't need to wait hours.

---

### Post by sagent3000 on 2014-08-12
thanks for the response. i have tried it several times and it STILL hangs. its been hanging since 8am and its now 12hrs later.  any other suggestions?

---

### Post by sagent3000 on 2014-08-13
I tried it again and interrupted it in the middle to see if i could get information and this is what i get 

> dpkg --configure -aSetting up nautilus-dropbox (0.7.1-2) ...


Dropbox is the easiest way to share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)


^CTraceback (most recent call last):
  File "/usr/bin/dropbox", line 1384, in <module>
    ret = main(sys.argv)
  File "/usr/bin/dropbox", line 1373, in main
    result = commands[argv[i]](argv[i+1:])
  File "/usr/bin/dropbox", line 806, in update
    download()
  File "/usr/bin/dropbox", line 529, in download
    download = DownloadState()
  File "/usr/bin/dropbox", line 248, in __init__
    self.socket = urllib.urlopen("http://www.dropbox.com/download?plat=%s" % plat())
  File "/usr/lib/python2.7/urllib.py", line 86, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 358, in open_http
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 664, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 634, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 660, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 436, in open_https
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 1161, in connect
    self.sock = ssl.wrap_socket(sock, self.key_file, self.cert_file)
  File "/usr/lib/python2.7/ssl.py", line 381, in wrap_socket
    ciphers=ciphers)
  File "/usr/lib/python2.7/ssl.py", line 143, in __init__
    self.do_handshake()
  File "/usr/lib/python2.7/ssl.py", line 305, in do_handshake
    self._sslobj.do_handshake()
KeyboardInterrupt
dpkg: error processing nautilus-dropbox (--configure):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 nautilus-dropbox



If i let it run to 100% and wait and press cntrl C then i get 
> 
Setting up nautilus-dropbox (0.7.1-2) ...


Dropbox is the easiest way to share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)


Downloading Dropbox... 100%^CTraceback (most recent call last):
  File "/usr/bin/dropbox", line 1384, in <module>
    ret = main(sys.argv)
  File "/usr/bin/dropbox", line 1373, in main
    result = commands[argv[i]](argv[i+1:])
  File "/usr/bin/dropbox", line 806, in update
    download()
  File "/usr/bin/dropbox", line 534, in download
    progress = one_chunk.next()[0]
  File "/usr/bin/dropbox", line 209, in download_file_chunk
    chunk = os.read(f.fileno(), 4096)
  File "/usr/lib/python2.7/socket.py", line 313, in fileno
    return self._sock.fileno()
  File "/usr/lib/python2.7/socket.py", line 224, in meth
    return getattr(self._sock,name)(*args)
KeyboardInterrupt
dpkg: error processing nautilus-dropbox (--configure):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 nautilus-dropbox


ANY suggestions???

---

