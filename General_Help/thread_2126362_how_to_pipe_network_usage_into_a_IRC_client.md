---
title: "how to pipe network usage into a IRC client?"
date: 2013-03-16
forum: General Help
---

### Post by cain071546 on 2013-03-16
ive been using Quassel as my IRC client for a while
its nice and all but i have a friend who is using windows and mIRC
and he has a script that displays his Servers Network Usage into the IRC


<DsT> &#149;&#155;&#155; Download: 14.65 MB/s ::: Upload: 594.31 KB/s «


looks like that

it has to be possible for me to replicate this somehow
any scriptable clients you reccomend?
Thanx

---

### Post by andrew.46 on 2013-03-17
irssi has a script called nact.pl which I installed briefly which looks like it can do this and more:

```

  32 #  Add something like this to your theme file to customize to look of the item
  33 #
  34 #    nact_display = "$0%R>%n%_$1%_%G>%n$2";
  35 #    
  36 #  where $0 is the input, $1 the device and $2 the output. To customize the
  37 #  outout of the /bw command add something like
  38 #
  39 #    nact_command = "$0)in:$1:out($2";
  40 #
  41 #  to your theme file.
  42 #
  43 ##########
  44 # THEME
  45 ####
  46 #
  47 # This is the complete list of parameters passed to the format:
  48 #
  49 #    $0: incomming rate
  50 #    $1: name of the device, eg. eth0
  51 #    $2: outgoing rate
  52 #    $3: total bytes received
  53 #    $4: total bytes sent
  54 #    $5: sum of $4 and $5

```

My screenshot shows only the bare details, I have not fiddled all that much with it :)

---

