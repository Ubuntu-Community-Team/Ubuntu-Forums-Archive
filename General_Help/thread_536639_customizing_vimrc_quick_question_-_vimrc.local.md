---
title: "customizing vimrc quick question - vimrc.local???"
date: 2007-08-28
forum: General Help
---

### Post by jf/ on 2007-08-28
hi guys, I'm just a bit confused about the usage of vimrc.local in ubuntu, and would like to have some clarification. As a matter of habit/preference, I usually go ahead and edit the system-wide vimrc in any installation that i setup, but i can't help but think about whether this would be "the ubuntu way" of going about doing things...

furthermore, the following lines in /etc/vim/vimrc leave me wondering...

```
" Source a global configuration file if available
" XXX Deprecated, please move your changes here in /etc/vim/vimrc
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

```

So do i still code my local changes in vimrc.local, or would u recommend that i just go ahead, and do it in the system vimrc instead?

---

### Post by aJayRoo on 2007-08-28
Personally I like to make any changes by creating a file '.vimrc' in my home directory. Obviously that only affects my user but if that is all you need to do then this is the approach I would recommend. I usually copy the template file ('/usr/share/vim/vim70/vimrc_example.vim') to a file named '.vimrc' in my home directory then make any changes I require.

---

### Post by jf/ on 2007-08-28
> **aJayRoo said:**
> Personally I like to make any changes by creating a file '.vimrc' in my home directory. Obviously that only affects my user but if that is all you need to do then this is the approach I would recommend. I usually copy the template file ('/usr/share/vim/vim70/vimrc_example.vim') to a file named '.vimrc' in my home directory then make any changes I require.

I'm looking to make system-wide changes, actually (hence the question), but I know what you mean...

---

### Post by aJayRoo on 2007-08-28
Ah right, fair enough, I got a bit confused! I usually make system wide changes to the /etc/vimrc file. I have actually never heard of vimrc.local, and I don't have that line you mention in my global vimrc file. I'm using version 7, perhaps that could explain a difference.

---

### Post by jf/ on 2007-08-28
thanks. Version 7? yeah, I'm using v7(.something) of vim as well. I'm assuming you're using Feisty? Did you do an upgrade from an earlier version, or is this from a fresh feisty install?

---

### Post by aJayRoo on 2007-08-28
Ah I just realised I checked that file on a system running Fedora 7! I do have that line in my system vimrc on Ubuntu (which is located at /etc/vim/vimrc as you said!). I think the section you quoted is recommending that changes should be made directly into the '/etc/vim/vimrc' file. As I said before this is the method I would recommend also. Sorry for the confusion!

---

### Post by jf/ on 2007-08-28
> **aJayRoo said:**
> Ah I just realised I checked that file on a system running Fedora 7! I do have that line in my system vimrc on Ubuntu (which is located at /etc/vim/vimrc as you said!). I think the section you quoted is recommending that changes should be made directly into the '/etc/vim/vimrc' file. As I said before this is the method I would recommend also. Sorry for the confusion!
heey, no prob, man!!! I appreciate your input and help on this question...

---

### Post by jf/ on 2007-08-28
> **aJayRoo said:**
> I do have that line in my system vimrc on Ubuntu (which is located at /etc/vim/vimrc as you said!). I think the section you quoted is recommending that changes should be made directly into the '/etc/vim/vimrc' file. As I said before this is the method I would recommend also.

anyway, if this is so, I wonder why... Anybody any idea? Why is vimrc.local no longer recommended?

---

