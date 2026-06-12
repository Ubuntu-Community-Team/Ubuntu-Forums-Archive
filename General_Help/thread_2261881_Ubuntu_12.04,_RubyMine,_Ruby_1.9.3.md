---
title: "Ubuntu 12.04, RubyMine, Ruby 1.9.3"
date: 2015-01-21
forum: General Help
---

### Post by msousa on 2015-01-21
Hi

I having a bit of trouble getting RubyMine working on my Ubuntu 12.04 pc. I have Ruby 1.9.3p0, RubyMine 7.0.2 installed.

```

~/RubyMine-7.0.2$ ruby -v
ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux]
~/RubyMine-7.0.2

```

In RubyMine I get 'RubyMine Gem Manager - RubyMine has detected that some of the gems required are not installed - Install missing gems'

When I select Install missing gems a popup comes up that says:
```

'Following gems were not installed:
bundler: Home path (C:/Ruby193/bin/ruby.exe) for ruby SDK 'ruby-1.9.3-p448' doesn't exist.'

```

I'm not sure where to go from here. Any ideas? Thanks...

---

### Post by mörgæs on 2015-01-22
I don't know Ruby but it seems like you are trying to install Windows software. 

If someone should be able to help please describe in all details how you have tried installing.

---

### Post by msousa on 2015-01-23
> **mörgæs said:**
> I don't know Ruby but it seems like you are trying to install Windows software. 

If someone should be able to help please describe in all details how you have tried installing.

I downloaded the RubyMine 7.0.02 linux version from [https://www.jetbrains.com/ruby/download/](https://www.jetbrains.com/ruby/download/) and installed a code base from someone who develops on windows, unfortunately that left some windows looking stuff. I've since been able to get past some of that, but now am experiencing other issues that I feel are just linux based.
 
In the settings under Ruby SDK and Gems, the only ruby mentioned  there is ruby-1.9.3-p0. There is a long list of gems in the window next  to it.

There  doesn't appear to be any errors in the ruby code (nothing shows up as  red - there are warnings). When I press the run or debug buttons, in the  Console I get the following:
```
Fast Debugger (ruby-debug-ide 0.4.24, ruby-debug-base19x 0.11.30.pre15) listens on 127.0.0.1:42094
Uncaught exception: Bundler could not find compatible versions for gem "bundler":
  In Gemfile:

    rails (= 4.0.0) depends on
      bundler (< 2.0, >= 1.3.0)

  Current Bundler version:
    bundler (1.0.15)
``` 

I have a 'bundle' under /usr/bin/X11 that is 1.0.15 (bundler and bundle seem to go hand-in-hand), so I'm thinking it is using that one, but when I ask which bundle in being used is says the 1.7.12 version:
```
$ which bundle
/usr/local/bin/bundle
$ /usr/local/bin/bundle -v
Bundler version 1.7.12
$
$ /usr/bin/X11/bundle -v
Bundler version 1.0.15
$
```

Here's some of the versions:
```
$ bundle -v
Bundler version 1.7.12
$
$ bundler -v
Bundler version 1.7.12
$
$ ruby -v
ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux]
$
```

I'm not sure if this is helpful, but here is what I have for Ruby:
```
$ whereis ruby
ruby: /usr/bin/ruby /usr/bin/ruby1.8 /usr/lib/ruby /usr/bin/X11/ruby /usr/bin/X11/ruby1.8 /usr/share/man/man1/ruby.1.gz
$
$ which ruby
/usr/bin/ruby
$

```

I don't why it would use the /usr/bin/X11/bundle (if in fact, that's what it is doing), or how to check that it is doing that in RubyMine, or if that is actually the problem? I do need RubyMine to start using the one in /usr/local/bin.

Any help would be greatly appreciated. Thanks...

---

