---
title: "Issue with Ruby after Install of 12.10"
date: 2012-10-20
forum: General Help
---

### Post by RevDavid on 2012-10-20
Hello,

I am having some issues with Ruby after installing Ubuntu 12.10. whenever I trying installing a gem package i get errors and have no idea how to fix them. Below is what I am getting

```
david@Ubuntu-Laptop:~$ sudo gem install sqlite3
Building native extensions.  This could take a while...
ERROR:  Error installing sqlite3:
	ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
	from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
	from extconf.rb:3:in `<main>'


Gem files will remain installed in /var/lib/gems/1.9.1/gems/sqlite3-1.3.6 for inspection.
Results logged to /var/lib/gems/1.9.1/gems/sqlite3-1.3.6/ext/sqlite3/gem_make.out

```

If anyone can shed some light on this I would appreciated it :)

Thank you.

---

### Post by mariosant on 2012-10-20
Have you tried to install the required packages?

sudo apt-get install libsqlite3-dev

What ruby version are you using and how did you acquire it?

---

### Post by RevDavid on 2012-10-21
So sorry for the delay, was working late last night. As far as the Ruby version I am using I tried 1.9.1 and 1.9.3. 

I originally installed through the software center and then also from command line just to be safe. I installed the sqlite3-dev and that didn't help.

I tried starting a new program with rails and it seems to set the application up but then I get permission error's as well saying I can't access certain area aand have to be root. So, I looked in Nautilus and the folder that was created has a lock on it and I can't delete or change anything unless I am root.

This is a fresh install and not sure what is going on. I even tried Linux Mint just to see what happens and get the same thing on a fresh install of that.

---

### Post by RevDavid on 2012-10-25
Good afternoon everyone, 

A quick update. After downloading several package's which include:

[LIST]
[*]Ruby 1.9.3
[*]Rails 3.2
[*]Ruby Gems
[*]Ruby-Railities
[*]Bundle
[/LIST]


I cannot get a application to generate correctly. Rails will setup the application but rec error message when trying to do a bundle install which shows....

```

/usr/bin/ruby1.9.1: No such file or directory -- /usr/bin/bundle (LoadError)
```


Them when I install the bundle with "sudo gem install bundle" I get this...

```
1 gem installed
Installing ri documentation for bundle-0.0.1...
file 'lib' not found
Installing RDoc documentation for bundle-0.0.1...
file 'lib' not found
```


Then if I try running "bundle Install" I get this...

```
Could not locate Gemfile
```


Now I am seeing these files installed on my hard drive in the usr/bin area but still will not work. I even went as far as wiping my whole drive and doing a fresh install of the OS and the programs and still same issue. If anyone can be of assistance I would truly appreciate it.

---

### Post by madAndroid on 2012-10-29
Have you tried to set your ruby version using the alternatives system?

```

update-alternatives --config ruby

```

---

