---
title: "problems running python script in browser"
date: 2013-12-29
forum: General Help
---

### Post by nev.dowling on 2013-12-29
I'm a novice at Linux & Python but working through Mike McGraths book "[Python in easy steps]("http://ineasysteps.com/products-page/programming/python-in-easy-steps/")" using Ubuntu 12.04 LTS.  First installed python3 (V3.2.3), and the default python 2.7.3 remains installed. I've been able to execute all the programming exercises (using python3 & some also run on python) until Chapter 8: Processing Requests, which requires [Apache2]("https://help.ubuntu.com/12.04/serverguide/httpd.html#http-installation") with [mod_python ]("http://grisha.org/blog/2013/10/25/mod-python-the-long-story/"). I used the [procedure]("http://ubuntuforums.org/showthread.php?t=1193983&p=7498335#post7498335") from [                                              ]("http://ubuntuforums.org/member.php?u=120996")                                                                                     [**[COLOR=#000000]curvedinfinity[/COLOR]**]("http://ubuntuforums.org/member.php?u=120996") in [these forums]("http://ubuntuforums.org/showthread.php?t=1193983&p=7498335#post7498335") to install and configure mod_python.  When I enter [http://localhost/index](http://localhost/index) the /var/www/index.html file runs and displays on the webpage.  When I enter [http://localhost/hello1.py](http://localhost/hello1.py) the script from /var/www/hello1.py runs but fails due to errors - in short MOD_PYTHON Error, TypeError: index() takes exactly 1 argument (0 given) and it appears the script is being interpreted using python 2.7 as the traceback shows "File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch     default=default_handler, arg=req, silent=hlist.silent)" and others.  This is OK as I understand that script has a problem when run using python2.x but the real issue I'm having is that another script (/var/www/fibonacci.py - that runs without error from the command line) fails to execute from the browser, indeed the file is not even found??  

[http://localhost/fibonacci.py](http://localhost/fibonacci.py)
**Not Found**

 The requested URL /fibonacci.py was not found on this server.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at localhost Port 80


VGN-CR25G-R:/var/www$ more fibonacci.py
#
a, b = 0,1
#
# while loop
#
while b < 100 :                
    print (b)
    a,b = b, a+ b
print (a)    
VGN-CR25G-R:/var/www$ 
VGN-CR25G-R:/var/www$ python3 fibonacci.py 
1
1
2
3
5
8
13
21
34
55
89
89

the /var/log/apache2/error.log has the following:

[Sun Dec 29 11:36:18 2013] [error] [client 127.0.0.1] TypeError: index() takes exactly 1 argument (0 given)
[Sun Dec 29 11:40:39 2013] [notice] caught SIGTERM, shutting down
[Sun Dec 29 11:40:40 2013] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Sun Dec 29 11:40:40 2013] [error] python_init: Python executable found '/usr/bin/python'.
[Sun Dec 29 11:40:40 2013] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Sun Dec 29 11:40:40 2013] [notice] mod_python: Creating 8 session mutexes based on 6 max processes and 25 max threads.
[Sun Dec 29 11:40:40 2013] [notice] mod_python: using mutex_directory /tmp 
[Sun Dec 29 11:40:40 2013] [notice] Apache/2.2.22 (Ubuntu) mod_python/3.3.1 Python/2.7.3 configured -- resuming normal operations
[

Can anyone help so that I can run the /var/www/fibonacci.py file using the webbrowser - [http://localhost/fibonacci.py](http://localhost/fibonacci.py) ??  It would also help if apache2 mod_python could be configured to use python3.

---

### Post by J_Me on 2013-12-29
As your just starting with python you really shouldn’t concern yourself with python3, once you've grasped the python language it's easy to work with the latest version number. There's a ton of free books online about python [http://learnpythonthehardway.org/book/](http://learnpythonthehardway.org/book/) and [http://wiki.python.org/moin/IntroductoryBooks](http://wiki.python.org/moin/IntroductoryBooks). Also don't uninstall python2.7 Ubuntu uses it internally and you'll be left with a blank desktop. I don't know if you have specific reasons for running python in a web browser but you can use the terminal to run python programs just type in 'python'(for 2.7) or 'python3.2'(for 3.2) and your in, or run a python text file with 'python yourFile.py'.  cheers

---

### Post by nev.dowling on 2013-12-29
I heeded the same caution - "Don't remove the default 2.7 version of Python from your system in case some applications depend upon it" from the 2013 instruction book ([Python - in easy steps]("http://ineasysteps.com/products-page/programming/python-in-easy-steps/")) and I have run some of the exercises using both versions of Python, but the book is based on Python3 so that's why I'm using it. Although the book demonstrates Python installation on both Linux & Windows the subsequent chapters use a Windows example, whereas I continued on with Ubuntu.  Chapter 8 is about running python from a web browser, which is why I'm using Apache and mod_python, the book suggests using Abyss Personal Edition from [www.aprelium.com]("http://www.aprelium.com") for a windows server.  It's confusing that I can see results from one failing script (/var/www/hello1.py) in the web browser, but another script that runs error free in the Terminal (/var/www/fibonacci.py) cannot even be found by the web browser?

---

