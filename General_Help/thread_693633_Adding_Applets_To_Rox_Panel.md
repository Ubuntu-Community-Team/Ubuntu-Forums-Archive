---
title: "Adding Applets To Rox Panel"
date: 2008-02-11
forum: General Help
---

### Post by Mark76 on 2008-02-11
I have the task tray and clock applets downloaded but I can't quite work out how to integrate them into the Rox panel.

Anyone? :confused:

---

### Post by kerry_s on 2008-02-11
> **Mark76 said:**
> I have the task tray and clock applets downloaded but I can't quite work out how to integrate them into the Rox panel.

Anyone? :confused:


have you tried just starting them up and dragging them on to the panel. rox is drag and drop oriented.

---

### Post by Mark76 on 2008-02-11
I downloaded the Rox-All package and, yep, drag and drop works.

Now... Who do I bitch to about getting the pager and sys tray working? ;)

And where do I go to change the backgrounds of the applets?

---

### Post by kerry_s on 2008-02-11
> **Mark76 said:**
> I downloaded the Rox-All package and, yep, drag and drop works.

Now... Who do I bitch to about getting the pager and sys tray working? ;)

And where do I go to change the backgrounds of the applets?


so you got them on the panel, but they don't work?

applets background, you mean the panel color?

could i get a screen shot? i would like to see your setup.

if you don't know how:
sudo apt-get install scrot

in term> scrot 1.jpg

---

### Post by Mark76 on 2008-02-11
Sure, why not? :D

And yes, I do mean the panel colour.

---

### Post by Mark76 on 2008-02-11
What the hell is this Rox-Lib2 thing I keep being asked for?

---

### Post by kerry_s on 2008-02-11
nice

the panels are part of the gtk theme, so you would probably just put the right lines in ~/.gtkrc2.0

not sure what the lines are, i've only changed my rox background and don't use rox panels. try looking at the rox site, i'll check in a bit, after i walk my dogs. :)

---

### Post by Mark76 on 2008-02-11
Your panel.. She is big senor!

---

### Post by kerry_s on 2008-02-11
> **Mark76 said:**
> Your panel.. She is big senor!

yeah, i made them big for my niece, not very good vision thick *ss glasses. she's been doing her homework on my computer. i usually don't have icons in the top left, i put those for her to do math and a couple of report's. you know that the kids can do there homework on line now? man, they didn't have that in my day.

here's a clear shot

---

### Post by kerry_s on 2008-02-11
it would normally look something like this->

---

### Post by kerry_s on 2008-02-11
> **Mark76 said:**
> What the hell is this Rox-Lib2 thing I keep being asked for?

it's here-> [http://roscidus.com/desktop/ROX-Lib](http://roscidus.com/desktop/ROX-Lib)

here is for the panel-> [http://roscidus.com/desktop/node/182](http://roscidus.com/desktop/node/182)

alright catch ya later, i'm going to change my rox window icons. :)

---

### Post by Mark76 on 2008-02-11
As you can see, I already modded the main panel (what? You thought it was orange by default? :lol:), so what I'm really after is the modification I need to make to get the applet panels to match

---

### Post by Mark76 on 2008-02-11
Please explain this, someone

---

### Post by kerry_s on 2008-02-11
> **Mark76 said:**
> As you can see, I already modded the main panel (what? You thought it was orange by default? :lol:), so what I'm really after is the modification I need to make to get the applet panels to match

yeah, it's the same thing, you just need to use the correct gtk-name for the applet, if you got any gtk themes installed you can try looking in them for the applet name or google.

no idea on the compile, to me it looks like you have a version mismatch.

---

### Post by kerry_s on 2008-02-11
i dressed up my rox, what do ya think?

---

### Post by Mark76 on 2008-02-11
Not bad ;)

Do you have any idea where I can get the public key from?  I got this error recently

> Error fetching 'AE07828059A53CC1.gpg':

No valid signatures found. Signatures:
- ERROR signature by AE07828059A53CC1: Unknown key. Try 'gpg --recv-key AE07828059A53CC1'

---

### Post by kerry_s on 2008-02-11
what repo have you added?

---

### Post by Mark76 on 2008-02-11
None. Which one should I have?

---

### Post by kerry_s on 2008-02-11
post your /etc/apt/sources.list

mine would do you no good, i'm running debian etch/lenny custom install.

---

### Post by Mark76 on 2008-02-11
Okay.

Attached below

---

### Post by kerry_s on 2008-02-11
> **Mark76 said:**
> Okay.

Attached below

looks alright to me, you should turn off the cdrom though,so you don't have to stick it in each time.

try again with synaptic> sudo synaptic <turn off you cdrom repo first though.

---

### Post by fox_xyzzy on 2008-02-12
> **Mark76 said:**
> Not bad ;)

Do you have any idea where I can get the public key from?  I got this error recently

It should get the key automatically. Try running it with logging, e.g. by entering this command in a terminal:

```
$ 0launch -vvc http://rox.sourceforge.net/2005/interfaces/ROX-Filer
```

What does it print?

See also:

[http://roscidus.com/desktop/node/900#comment-15404](http://roscidus.com/desktop/node/900#comment-15404)

---

### Post by Mark76 on 2008-02-12
This is the output from the terminal (note, I would have saved it as a txt file and uploaded it, but there doesn't seem to be a save function in the terminal)

> 0launch -vvc [http://rox.sourceforge.net/2005/interfaces/ROX-Filer](http://rox.sourceforge.net/2005/interfaces/ROX-Filer)
Traceback (most recent call last):
  File "logging/__init__.py", line 744, in emit
    msg = self.format(record)
  File "logging/__init__.py", line 630, in format
    return fmt.format(record)
  File "logging/__init__.py", line 418, in format
    record.message = record.getMessage()
  File "logging/__init__.py", line 288, in getMessage
    msg = msg % self.args
TypeError: not all arguments converted during string formatting
INFO:root:Running 0launch 0.29 ['http://rox.sourceforge.net/2005/interfaces/ROX-Filer']; Python 2.5.1 (r251:54863, Oct  5 2007, 13:50:07) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]
DEBUG:root:Supported systems: '{None: 2, 'Linux': 1}'
DEBUG:root:Supported processors: '{None: 1, 'x86_64': 0}'
DEBUG:root:Recalculate! root = [http://rox.sourceforge.net/2005/interfaces/ROX-Filer](http://rox.sourceforge.net/2005/interfaces/ROX-Filer)
DEBUG:root:Initialising new interface object for [http://rox.sourceforge.net/2005/interfaces/ROX-Filer](http://rox.sourceforge.net/2005/interfaces/ROX-Filer)
DEBUG:root:Interface not cached and not off-line. Downloading...
DEBUG:root:Recalculate! root = [http://rox.sourceforge.net/2005/interfaces/ROX-Filer](http://rox.sourceforge.net/2005/interfaces/ROX-Filer)
DEBUG:root:Interface not cached and not off-line. Downloading...
DEBUG:root:begin_iface_download <Interface http://rox.sourceforge.net/2005/interfaces/ROX-Filer> (force = 0)
DEBUG:root:Need to download
DEBUG:root:get_best_implementation(<Interface http://rox.sourceforge.net/2005/interfaces/ROX-Filer>), with feeds: []
INFO:root:Interface <Interface http://rox.sourceforge.net/2005/interfaces/ROX-Filer> has no implementations!
DEBUG:root:No implementation chould be chosen yet
INFO:root:Currently downloading:
INFO:root:- [http://rox.sourceforge.net/2005/interfaces/ROX-Filer](http://rox.sourceforge.net/2005/interfaces/ROX-Filer)
INFO:root:Fetching key from [http://rox.sourceforge.net/2005/interfaces/AE07828059A53CC1.gpg](http://rox.sourceforge.net/2005/interfaces/AE07828059A53CC1.gpg)
INFO:root:Currently downloading:
INFO:root:- [http://rox.sourceforge.net/2005/interfaces/AE07828059A53CC1.gpg](http://rox.sourceforge.net/2005/interfaces/AE07828059A53CC1.gpg)
INFO:root:Importing key for feed 'http://rox.sourceforge.net/2005/interfaces/ROX-Filer'
WARNING:root:Failed to import key for 'http://rox.sourceforge.net/2005/interfaces/ROX-Filer': Errors from 'gpg --import':
gpg: failed to create temporary file `/home/mark/.gnupg/.#lk0x6e5460.Panopticon.12729': Permission denied
gpg: keyblock resource `/home/mark/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/mark/.gnupg/.#lk0x6e9540.Panopticon.12729': Permission denied
gpg: keyblock resource `/home/mark/.gnupg/pubring.gpg': general error
gpg: no writable keyring found: eof
gpg: error reading `[stdin]': general error
gpg: import from `[stdin]' failed: general error
Traceback (most recent call last):
  File "/usr/bin/0launch", line 4, in <module>
    cli.main(sys.argv[1:])
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/cli.py", line 304, in main
    _normal_mode(options, args)
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/cli.py", line 208, in _normal_mode
    policy.download_and_execute(prog_args, refresh = bool(options.refresh), main = options.main)
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/autopolicy.py", line 85, in download_and_execute
    self.recalculate_with_dl()
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/autopolicy.py", line 81, in recalculate_with_dl
    self.handler.wait_for_downloads()
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/handler.py", line 54, in wait_for_downloads
    dl.error_stream_closed()
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/download.py", line 148, in error_stream_closed
    x(stream)
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/iface_cache.py", line 95, in <lambda>
    dl.on_success.append(lambda stream: self._downloaded_key(dl, stream))
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/iface_cache.py", line 125, in _downloaded_key
    self.download_callback()
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/policy.py", line 194, in <lambda>
    pending.begin_key_downloads(self.handler, lambda pending = pending: self._keys_ready(pending))
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/policy.py", line 207, in _keys_ready
    self.handler.confirm_trust_keys(iface, pending.sigs, pending.new_xml)
  File "/usr/lib/python2.5/site-packages/zeroinstall/injector/handler.py", line 87, in confirm_trust_keys
    ''.join(['\n- ' + str(s) for s in sigs]))
zeroinstall.SafeException: No valid signatures found. Signatures:
- ERROR signature by AE07828059A53CC1: Unknown key. Try 'gpg --recv-key AE07828059A53CC1'


---

### Post by kerry_s on 2008-02-12
for terminal to text just add " > name.txt " to the end
example:
man rox > rox-man.txt

it will be in your ~/ directory
i use it all the time cause i prefer to read in my text editor. :)

fox_xyzzy, i hope you can help him. i'm going to leave it to you. :)

---

### Post by fox_xyzzy on 2008-02-13
```
gpg: failed to create temporary file `/home/mark/.gnupg/.#lk0x6e5460.Panopticon.12729': Permission denied
gpg: keyblock resource `/home/mark/.gnupg/secring.gpg': general error
```

Problem was that ~mark/.gnupg was owned by root, so the key couldn't be imported.

---

