---
title: "How to find out version of snap-packaged application?"
date: 2023-02-03
forum: General Help
---

### Post by ronzo on 2023-02-03
How can I find out which version a snap-packaged application has? I am not interested in the version number of the snap package itself but in the version the software it contains.

Let's take firefox for example. [https://packages.ubuntu.com/kinetic/firefox](https://packages.ubuntu.com/kinetic/firefox) only shows snap package details. But is it firefox 108 or 109? I cannot tell from the information given. Can you?

---

### Post by donald187 on 2023-02-03
If it's installed on your system run in the terminal

```

snap info firefox

```

Here's my output.

```

$ snap info firefox
name:      firefox
summary:   Mozilla Firefox web browser
publisher: Mozilla&#10003;
store-url: https://snapcraft.io/firefox
contact:   https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla
license:   unset
description: |
  Firefox is a powerful, extensible web browser with support for modern web
  application technologies.
commands:
  - firefox
  - firefox.geckodriver
snap-id:      3wdHCAVyZEmYsCMFDE9qt92UV8rC8Wdk
tracking:     latest/stable/ubuntu-22.04
refresh-date: 2 days ago, at 07:38 PST
channels:
  latest/stable:    109.0.1-1    2023-01-31 (2311) 250MB -
  latest/candidate: 109.0.1-1    2023-01-28 (2311) 250MB -
  latest/beta:      110.0b9-1    2023-02-03 (2330) 189MB -
  latest/edge:      111.0a1      2023-02-03 (2333) 196MB -
  esr/stable:       102.7.0esr-1 2023-01-17 (2270) 183MB -
  esr/candidate:    102.7.0esr-1 2023-01-09 (2270) 183MB -
  esr/beta:         &#8593;                                    
  esr/edge:         &#8593;                                    
installed:          109.0.1-1               (2311) 250MB -

```

The line beginning with installed says 109.0.1-1.

---

### Post by donald187 on 2023-02-03
Or if it's not installed on your system use

```

snap find firefox

```

---

### Post by howefield on 2023-02-03
Try the snap find command..

```
snap find firefox
```

---

### Post by him610 on 2023-02-04
> How can I find out which version a snap-packaged application has?
```
$ snap list 
```
Note: Ignore the bottom line of output since you are not interested in version of snapd.

---

