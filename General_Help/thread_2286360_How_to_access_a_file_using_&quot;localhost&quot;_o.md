---
title: "How to access a file using &quot;localhost&quot; or &quot;file&quot;"
date: 2015-07-11
forum: General Help
---

### Post by Ralph L on 2015-07-11
I would like to be able to access a file on my computer through wget so I tried the following tests:  I am under the impression, maybe wrongly so, that I can access a file on my computer using something like:
```
ralph@lat1:~$ cat http://localhost/test
cat: http://localhost/test: No such file or directory
```or ```
ralph@lat1:~$ cat file://localhost/test
cat: file://localhost/test: No such file or directory
```  I placed the file "test" in the highest level directory along with /bin, /etc, /usr, etc.  It is owned by root, has group root, permissions of read, write, execute for owner, group, and other--basically every permission is set.  However, every time I execute the cat commands I get "No such file or directory".  I CAN access the file with:```
ralph@lat1:~$ cat /test
This is a test at root level.
```  My /etc/hosts file reads:```
ralph@lat1:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	lat1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```  Is there anyway to access a file on my computer this way??  Any help is appreciated...

---

### Post by steeldriver on 2015-07-11
AFAIK that would require the files to be served by an http server - there is the python SimpleHTTPServer for example

You would then retrieve files using wget or curl (rather than cat)

---

### Post by dragonfly41 on 2015-07-11
Possibly a protocol handler might meet your requirements?

Here is one tutorial .. [http://askubuntu.com/questions/330937/is-it-possible-to-open-an-ubuntu-app-from-html](http://askubuntu.com/questions/330937/is-it-possible-to-open-an-ubuntu-app-from-html)

The "app" would open your file.

---

### Post by Ralph L on 2015-07-27
Thanks for the responses... I have been busy and have just now followed up on this thread.  The following made the folder "foo" available on the Internet.[CODEralph@lat1:~$ mkdir foo
ralph@lat1:~$ cd foo
ralph@lat1:~/foo$ touch foofile
ralph@lat1:~/foo$ python -m SimpleHTTPServer
Serving HTTP on 0.0.0.0 port 8000 ...
[/CODE]I accessed foo from Firefox by entering "http://localhost:8000" into Firefox address box.  I accessed ~foo/foofile by entering "http://localhost:8000/foofile" into Firefox's address box.  I was also able to use wget to copy foo (localhost:8000).  These web sites were helpful:  [http://www.2ality.com/2014/06/simple-http-server.html](http://www.2ality.com/2014/06/simple-http-server.html) , [http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python), [http://www.2ality.com/2014/06/simple-http-server.html](http://www.2ality.com/2014/06/simple-http-server.html), [http://www.gnu.org/software/wget/manual/wget.html#SEC_Contents](http://www.gnu.org/software/wget/manual/wget.html#SEC_Contents)

---

