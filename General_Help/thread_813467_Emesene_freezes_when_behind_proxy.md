---
title: "Emesene freezes when behind proxy"
date: 2008-05-30
forum: General Help
---

### Post by dr_james2k on 2008-05-30
Ok, so here's the problem.  Until recently I've been using pidgin and that works fine but I found out about emesene and it looks great.  However I'm behind a proxy which seems to cause the client to freeze when trying to log in then after the hang (of about 5 minutes) I get the error message:

> Error during login, please retry
(Login error:Authentication error: "Can't Connect to HTTPS server: (110,'Connection timed out')") 

I did manage to fix this yesterday by getting the latest version from the subversion repository, I was able to log in and use everything and it was great (the only problem was that none of my contacts could see my display picture - a small price to see what everyone is listening to.) but come today I'm back to the old hang when logging in then failure to logon.

When executing from the console I get this output:
> >>> VER 1 MSNP13 CVR0
Thread-2 doing VER 1 MSNP13 CVR0...
<<< VER 1 MSNP13 CVR0
>>> CVR 2 0x0c0a winnt 5.1 i386 MSNMSGR 8.0.0792 msmsgs [email]<my e-mail name>@hotmail.co.uk[/email]
Thread-2 doing CVR 2 0x0c0a winnt 5.1 i386 MSNMSGR 8.0....
<<< CVR 2 8.5.1302 8.5.1302 8.1.0178 [http://msgr.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe](http://msgr.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe) [http://get.live.com/es](http://get.live.com/es)
>>> USR 3 TWN I <my e-mail name>@hotmail.co.uk
Thread-2 doing USR 3 TWN I <my e-mail name>@hotmail.co.u...
<<< GCF 0 6289
Thread-2 doing poll...
<<< USR 3 TWN S ct=1212196103,rver=5.0.3270.0,wp=FS_40SEC_0_COMPACT,lc=1033,id=507,ru=http:%2F%2Fmessenger.msn.com,tw=0,kpp=1,kv=4,ver=2.1.6000.1,rn=1lgjBfIL,tpf=b0735e3a873dfb5e75054465196398e0
PASSPORT begin
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Thread-2 doing poll...
Session closed
Thread-2 closed
Traceback (most recent call last):
  File "/home/james/emesene/emesenelib/core.py", line 271, in _loginInputHandler
    retval = self._loginProcess(socket)
  File "/home/james/emesene/emesenelib/core.py", line 340, in _loginProcess
    self.passportid = self.passportAuth(hash)
  File "/home/james/emesene/emesenelib/core.py", line 510, in passportAuth
    str(e)
AuthError: Authentication error: "Can't connect to HTTPS server: (110, 'Connection timed out')"
login error ;_;
Login error: Authentication error: "Can\'t connect to HTTPS server: (110, \'Connection timed out\')"
Thread-2 closed


Any input on this would be greatly appreciated.

---

### Post by dr_james2k on 2008-06-01
Outside of my usual network where I don't need a proxy I can get emesene to work fine without any problems with the version offered in the hardy repository but as soon as I'm back in my normal network I have to turn the proxy on and it crashes, its so irritating not being able to use it all the time as it is my messenger of choice.

---

### Post by unicorn_2003_1 on 2008-06-01
Does your proxy server support "https"? maybe it's just "http, ftp, etc". 

I'm using emesene too, very promising app. Seems this has to do with either your proxy's https support or emesene itself.

Just my two cents.

---

### Post by dr_james2k on 2008-06-01
Yeah I'm using some other apps which use a https connection and there's no problem with them when the proxy is set up.

---

### Post by SaiHayashi on 2008-08-25
> **dr_james2k said:**
> Yeah I'm using some other apps which use a https connection and there's no problem with them when the proxy is set up.

yeah i had exactly the same problem sometimes when i connect thru my uni's wifi, but for me it happens more likely when i try to connect right when the wifi is connected, what i did was just to go to the option menu of emesene and ticked the "use http method" box and the problem is gone (at least for now).  Hope that helps.

---

### Post by SaiHayashi on 2008-08-25
> **dr_james2k said:**
> Yeah I'm using some other apps which use a https connection and there's no problem with them when the proxy is set up.

yeah i had exactly the same problem sometimes when i connect thru my uni's wifi, but for me it happens more likely when i try to connect right when the wifi is connected, what i did was just to go to the option menu of emesene and ticked the "use http method" box and the problem is gone (at least for now).  Hope that helps.

---

### Post by terryandtaotao on 2008-11-20
I have the same problem. It's just a basic no auth http proxy though I have other apps working behind proxy. Emesne just doesn't work with any proxy. Setting http_proxy in a terminal session doesn't help.

I think on OSX Messenger 7.x has the same stupid bug.

---

### Post by genius2002 on 2010-05-24
> **SaiHayashi said:**
> yeah i had exactly the same problem sometimes when i connect thru my uni's wifi, but for me it happens more likely when i try to connect right when the wifi is connected, what i did was just to go to the option menu of emesene and ticked the "use http method" box and the problem is gone (at least for now).  Hope that helps.

i meet the same problem.and solve it at your method!
thx:guitar:

---

