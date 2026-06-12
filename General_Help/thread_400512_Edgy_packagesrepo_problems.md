---
title: "Edgy packages/repo problems"
date: 2007-04-03
forum: General Help
---

### Post by ScatterBrain on 2007-04-03
I built an Edgy machine today (been stuck on dapper for a VERY long time) and a lot of things aren't working.

Vim is actually vim.tiny and not a full featured vim.  The default shell is no longer bash.

All that is well and good, except when I went to "correct" that, I found out that there seems to be a lot of dependency borkage when installing things.

For example, trying to install vim-full, fails with the no installable candidates for three additional packages (one of which is tcl)

**Error for vim-full:**
```
root@seti:~# apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  vim-common vim-tcl vim-ruby vim-python vim-perl vim-gtk vim-full
E: Package vim has no installation candidate

root@seti:~# apt-get install vim-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vim-full: Depends: vim-gui-common (= 1:7.0-035+1ubuntu5) but it is not installable
            Depends: vim-runtime (= 1:7.0-035+1ubuntu5) but it is not installable
            Depends: tcl8.4 (>= 8.4.5) but it is not installable
E: Broken packages
```
[B]
Error for ssh-server:[/B]
```
 root@seti:~# apt-get install ssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh-server is a virtual package provided by:
  ssh-krb5 3.8.1p1-10build1
  lsh-server 2.0.2-1
You should explicitly select one to install.
E: Package ssh-server has no installation candidate
```[B]

Error for boinc-app-seti[/B]:
```
root@seti:~# apt-get install boinc-app-seti
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  boinc-app-seti: Depends: fftw3 but it is not installable
E: Broken packages
```


Is there something wrong with the repositories, or is it just me?

---

### Post by NeoLithium on 2007-04-03
Have you enabled all of your repositories?
There's a good list here: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

(Just in case you haven't)

---

### Post by ScatterBrain on 2007-04-03
> **NeoLithium said:**
> Have you enabled all of your repositories?
There's a good list here: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

(Just in case you haven't)

Well that must have been it...

I changed my sources to the list shown in the link and all is well in the world now.  I can't believe I had to pull vim from the backports mirror.

Well, anyway thanks.  I'll move on now.

---

### Post by NeoLithium on 2007-04-03
No problem :) At least it's all sorted out, in the end.

---

