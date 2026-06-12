---
title: "Dell XPS13 9300 - Installing Fusuma for trackpad"
date: 2021-04-12
forum: General Help
---

### Post by exhile on 2021-04-12
If anyone can help, I am having trouble installing Fusuma for the track-pad on my XPS13.

The errors are as follows: 

```
joe@XPS13:~$ sudo gem update fusuma
Updating installed gems
Updating fusuma
Building native extensions. This could take a while...
ERROR:  Error installing fusuma:
    ERROR: Failed to build gem native extension.

    current directory: /var/lib/gems/2.7.0/gems/posix-spawn-0.3.15/ext
/usr/bin/ruby2.7 -I /usr/lib/ruby/2.7.0 -r ./siteconf20210412-24798-nt6p53.rb extconf.rb
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h

You might have to install separate package for the ruby development
environment, ruby-dev or ruby-devel for example.

extconf failed, exit code 1

Gem files will remain installed in /var/lib/gems/2.7.0/gems/posix-spawn-0.3.15 for inspection.
Results logged to /var/lib/gems/2.7.0/extensions/x86_64-linux/2.7.0/posix-spawn-0.3.15/gem_make.out
Gems updated: posix-spawn
Gems already up-to-date: fusuma


```

---

### Post by Xian on 2021-04-12
First let's reinstall ruby

```
sudo apt-get --reinstall install ruby
```

Then make sure the dev packages are installed

```
[FONT=inherit]sudo apt-get install ruby-dev[/FONT]
```

Now try again ..... any change?

---

### Post by exhile on 2021-04-13
> **Xian said:**
> First let's reinstall ruby

```
sudo apt-get --reinstall install ruby
```

Then make sure the dev packages are installed

```
[FONT=inherit]sudo apt-get install ruby-dev[/FONT]
```

Now try again ..... any change?

I put in the commands as you've suggested and receive the following: 

```
joe@XPS13:~$ sudo gem install fusuma
Building native extensions. This could take a while...
ERROR:  Error installing fusuma:
    ERROR: Failed to build gem native extension.

    current directory: /var/lib/gems/2.7.0/gems/posix-spawn-0.3.15/ext
/usr/bin/ruby2.7 -I /usr/lib/ruby/2.7.0 -r ./siteconf20210412-6124-1aq0q1a.rb extconf.rb
creating Makefile

current directory: /var/lib/gems/2.7.0/gems/posix-spawn-0.3.15/ext
make "DESTDIR=" clean
sh: 1: make: not found

current directory: /var/lib/gems/2.7.0/gems/posix-spawn-0.3.15/ext
make "DESTDIR="
sh: 1: make: not found

make failed, exit code 127

Gem files will remain installed in /var/lib/gems/2.7.0/gems/posix-spawn-0.3.15 for inspection.
Results logged to /var/lib/gems/2.7.0/extensions/x86_64-linux/2.7.0/posix-spawn-0.3.15/gem_make.out
joe@XPS13:~$ 


```

---

### Post by exhile on 2021-04-13
Can anyone help me??? Please....

---

### Post by Xian on 2021-04-13
Likely you just first need to install the build-essential package. 

```
[COLOR=#24292E][FONT=SFMono-Regular]sudo apt-get install build-essential[/FONT][/COLOR]
```

---

### Post by exhile on 2021-04-14
> **Xian said:**
> Likely you just first need to install the build-essential package. 

```
[COLOR=#24292E][FONT=SFMono-Regular]sudo apt-get install build-essential[/FONT][/COLOR]
```

It worked!!! Thank-you so much!

---

