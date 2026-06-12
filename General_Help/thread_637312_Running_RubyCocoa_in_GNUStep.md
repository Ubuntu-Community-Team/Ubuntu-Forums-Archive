---
title: "Running RubyCocoa in GNUStep?"
date: 2007-12-10
forum: General Help
---

### Post by LodeRunner on 2007-12-10
For various convoluted reasons, this might be the perfect answer to a project I'm involved in, except I'm not 100% sure if RubyCocoa can even be run in GNUStep.  The sourceforge page implies it can, but an archived message from 2002 says it can't.

What I've gotten so far:

```
$ ruby install.rb config
(eval):12: command not found: svnversion
install.rb: entering config phase...
libxml2 is not available!
create ext/rubycocoa/extconf.rb
create framework/GeneratedConfig.xcconfig
create framework/src/objc/Version.h
create tests/Makefile
---> framework
create /home/loderunner/Desktop/RubyCocoa-0.13.0/framework/src/objc/osx_ruby.h ...
create /home/loderunner/Desktop/RubyCocoa-0.13.0/framework/src/objc/osx_intern.h ...
BSROOT="/home/loderunner/Desktop/RubyCocoa-0.13.0/framework/bridge-support" CFLAGS="" /usr/bin/ruby1.8 build.rb
./gen_bridge_metadata.rb:36: cpp not found (RuntimeError)
        from build.rb:1:in `require'
        from build.rb:1
config failed
hook /home/loderunner/Desktop/RubyCocoa-0.13.0/framework/post-config.rb failed:
'system BSROOT="/home/loderunner/Desktop/RubyCocoa-0.13.0/framework/bridge-support" CFLAGS="" /usr/bin/ruby1.8 build.rb' failed
try 'ruby install.rb --help' for usage

```

libxml2 was already installed.  Installed libxml2-dev; same message. Not sure about the svnversion error.  cpp 4.1 is already installed--doesn't seem to be a dev version, so I suppose I probably need to downgrade or something.  But, I could error-hunting all night... Was wondering if someone here knew of a guide somewhere, or knew if it was even possible to do.

I know that [RIGS]("http://www.gnustep.org/experience/RIGS.html") is an alternative way of accessing Ruby via GNUStep, but it doesn't appear to have the same level of integration with Objective-C.  (Objective-C / Ruby integration is the primary goal here.)  However, my overall technical level isn't very high, so I could be mistaken.

Q: "If your overall technical level isn't very high, why on earth are you trying to implement an extension to a primarily-Macintosh programming environment in order to fuse together a lesser-known scripting language with a lesser-known C-derivative??"

A: The short version is: Because our technical expert/god is dead-set on using the D programming language, just to be different and cool (and no, I can't get rid of him. For one, he's my best friend.)  I'm pretty sure I can ween him off of the D-fixation using Ruby as a lure.  He loves using Ruby as a prototyping language (and I'm rather fond of it myself) , so I figure he won't be able to resist it if I show him a programming environment where he can prototype in Ruby, and slowly replace each object with Objective-C for the deployment version.  Ideally, I would like to be able to do this without buying a bunch of Macs.

Any information you could pass my way would be greatly appreciated.

EDIT: Yeah ok, it's complaining it can't find AddressBook now.  Doesn't seem to bode well...

---

