---
title: "How to install script to allow D11 remote to control mythTV"
date: 2007-08-06
forum: General Help
---

### Post by visionviper on 2007-08-06
I want to use the scripts found here: [http://www.rkroll.com/d11/](http://www.rkroll.com/d11/)

It will allow me to control MythTV using the remote for my D11 DirectTV box. I have limited knowledge of ubuntu (but I am really good at following guides! :P) so I don't know the first thing is getting this script ready to run. Could anyone here give me a hand?

And while I am at it, is there a guide somewhere I can follow to get the directtv.pl script working that allows MythTV to control my receiver? I haven't seemed to be able to get it working.

---

### Post by visionviper on 2007-08-07
I think I found the problem with the directv.pl script. The problem isn't really the script, but I am missing a cable. I am going to pick one up tomorrow and go from there.

I am still having problems with the other script though. I don't know how to set it up and use it because it doesn't come in a nice pre-packaged file with an install script :P

---

### Post by visionviper on 2007-08-07
I have gotten MythTV to run the script. I am now getting this error:

```

2007-08-07 11:53:43.035 ret_pid(5842) child(5842) status(0x7f00)
2007-08-07 11:53:43.036 ChannelBase: external tuning program exited with error 127

```

When I run the scripts start script directly, I get the following error:
```

ivtvctl: option requires an argument -- R
Unknown argument `(null)'
[: 7: <mode>: unexpected operator
kill: 11: Illegal number: #!/usr/bin/tclsh

```

I have ivtv-utils installed.

---

