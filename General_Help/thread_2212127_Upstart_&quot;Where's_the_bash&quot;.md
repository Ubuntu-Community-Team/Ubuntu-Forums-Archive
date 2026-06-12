---
title: "Upstart: &quot;Where's the bash?&quot;"
date: 2014-03-19
forum: General Help
---

### Post by BuntuSeriously on 2014-03-19
Greetings!

I've been working at getting a certain bash script to launch via Upstart with no success.  If it launches at all, it _WILL_ be with dash.

Here's what I've been trying:

```
# scriptFoo

description    "scriptFoo"

start on runlevel [2]

task
exec /etc/scriptFoo
```

...runs scriptFoo with dash; ignoring the bangline


```
# scriptFoo

description    "scriptFoo"

start on runlevel [2]

task
script

    bash -c '/etc/scriptFoo'

end script
```

...runs scriptFoo with dash; ignoring the bangline


```
# scriptFoo

description    "scriptFoo"

start on runlevel [2]

task
exec "bash -c '/etc/scriptFoo'"
```

...doesn't run scriptFoo at all


```
# scriptFoo

description    "scriptFoo"

start on runlevel [2]

task
exec bash -c '/etc/scriptFoo'
```

...runs scriptFoo with dash; ignoring the bangline


```
# scriptFoo

description    "scriptFoo"

start on runlevel [2]

task
script
/bin/bash <<EOT

    exec bash -c '/etc/scriptFoo'

EOT
end script
```

...runs scriptFoo with dash; ignoring the bangline


```
# scriptFoo

description    "scriptFoo"

start on runlevel [2]

task
script
/bin/bash <<EOT

    bash -c '/etc/scriptFoo'

EOT
end script
```

...runs scriptFoo with dash; ignoring the bangline


{Insert countless other permutations, including "start on filesystem" (runs with dash) and "start on started network-services" (doesn't run at all), and so forth *ad nauseam*}


FWIW, "scriptFoo" uses a bash builtin which is not available in dash.

SO, I'm well stuck.  Any thoughts?


Thanks!

---

### Post by Lars Noodén on 2014-03-19
The immediate idea that comes to my mind is to rework the script into something more standard so that it runs under dash.  

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

From what I gather, dash was chosen for SystemV because of speed in reducing startup times.  Upstart was chosen to further speed up startup.  

[http://lwn.net/Articles/343924/](http://lwn.net/Articles/343924/)

I guess there were enough cases that mattered to enough developers for the change to be made.  For machines that rarely reboot, it wouldn't matter much one way or the other.

---

