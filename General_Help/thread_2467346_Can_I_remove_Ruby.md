---
title: "Can I remove Ruby ?"
date: 2021-09-23
forum: General Help
---

### Post by oygle on 2021-09-23
I think I may have installed **Ruby** or Ruby on Rails for use with Jekyll ( [https://jekyllrb.com/](https://jekyllrb.com/) ), which involved **gem** and **bundler**

As I don't use Jekyll anymore (now Hugo - [https://gohugo.io/](https://gohugo.io/) ) , can I remove **Ruby**, and/or **gem**, and/or **bundler** ??  How do I find the dependancies ?

```
 gem list
```

> *** LOCAL GEMS ***

addressable (2.7.0)
benchmark (default: 0.1.0)
bigdecimal (default: 2.0.0)
bundler (2.2.19, default: 2.1.2)
cgi (default: 0.1.0)
colorator (1.1.0)
concurrent-ruby (1.1.9, 1.1.8)
csv (default: 3.1.2)
date (default: 3.0.0)
dbm (default: 1.1.0)
delegate (default: 0.1.0)
did_you_mean (default: 1.4.0)
em-websocket (0.5.2)
etc (default: 1.1.0)
eventmachine (1.2.7)
faraday (1.4.2)
faraday-em_http (1.0.0)
faraday-em_synchrony (1.0.0)
faraday-excon (1.1.0)
faraday-net_http (1.0.1)
faraday-net_http_persistent (1.1.0)
fcntl (default: 1.0.0)
ffi (1.15.1, 1.14.2)
fiddle (default: 1.0.0)
fileutils (default: 1.4.1)
forwardable (default: 1.3.1)
forwardable-extended (2.6.0)
gdbm (default: 2.1.0)
getoptlong (default: 0.1.0)
http_parser.rb (0.6.0)
i18n (1.8.10, 1.8.9, 0.9.5)
io-console (default: 0.5.3)
ipaddr (default: 1.2.2)
irb (default: 1.2.1)
json (default: 2.3.0)
kramdown (2.3.1, 2.3.0)
kramdown-parser-gfm (1.1.0)
liquid (4.0.3)
listen (3.5.1, 3.4.1)
logger (default: 1.4.2)
matrix (default: 0.2.0)
mercenary (0.4.0, 0.3.6)
minitest (5.13.0)
multipart-post (2.1.1)
mutex_m (default: 0.1.0)
net-pop (default: 0.1.0)
net-smtp (default: 0.1.0)
net-telnet (0.1.1)
observer (default: 0.1.0)
octokit (4.21.0)
open3 (default: 0.1.0)
openssl (default: 2.1.2)
ostruct (default: 0.2.0)
pathutil (0.16.2)
power_assert (1.1.7)
prime (default: 0.1.1)
pstore (default: 0.1.0)
psych (default: 3.1.0)
public_suffix (4.0.6)
racc (default: 1.4.16)
rake (13.0.1)
rb-fsevent (0.11.0, 0.10.4)
rb-inotify (0.10.1)
rdoc (default: 6.2.1)
readline (default: 0.0.2)
readline-ext (default: 0.1.0)
reline (default: 0.1.2)
rexml (3.2.5, 3.2.4, default: 3.2.3)
rouge (3.26.0)
rss (default: 0.2.8)
ruby2_keywords (0.0.4)
rubygems-update (3.2.19)
safe_yaml (1.0.5)
sass (3.7.4)
sass-listen (4.0.0)
sassc (2.4.0)
sawyer (0.8.2)
sdbm (default: 1.0.0)
singleton (default: 0.1.0)
stringio (default: 0.1.0)
strscan (default: 1.0.3)
terminal-table (2.0.0)
test-unit (3.3.5)
timeout (default: 0.1.0)
tracer (default: 0.1.0)
unicode-display_width (1.7.0)
uri (default: 0.10.0)
webrick (default: 1.6.0)
xmlrpc (0.3.0)
yaml (default: 0.1.0)
zlib (default: 1.1.0)


but where are these used, or how do I determine any dependancies, etc ??

---

### Post by TheFu on 2021-09-23
There is no core OS reason to have ruby installed on 20.04.
As for dependencies, you'll need to delve deep into the ruby system and APT to determine that.  Gems manually installed outside of APT have little use to an OS that doesn't use Ruby.
I would look for packages install via APT (or one of the many front-ends to it) that contain the term "ruby" in the name, as a first look effort.

If you want real issues, remove or try to upgrade python or perl on the system. That's a great way to end up with a system that cannot be booted.

---

### Post by oygle on 2021-09-23
> **TheFu said:**
> There is no core OS reason to have ruby installed on 20.04.
As for dependencies, you'll need to delve deep into the ruby system and APT to determine that.  Gems manually installed outside of APT have little use to an OS that doesn't use Ruby.
I would look for packages install via APT (or one of the many front-ends to it) that contain the term "ruby" in the name, as a first look effort..

Thanks for your reply. For some reason I saved the log file from the Jekyll installation and it does seem that was "why" I installed Ruby. There is a lot of libraries there.  Seems that install was the basis for adding in "bundler" as well, plus some mods to .bashrc

It may be a big rabbit hole to go down to try and determine what is installed, BUT do I use it, OR if I uninstall will it impact X,Y or Z ??

I may need to play it completely safe and wait until I do a clean install of Kubuntu; that will ensure that there are only packages residing that I need.

---

