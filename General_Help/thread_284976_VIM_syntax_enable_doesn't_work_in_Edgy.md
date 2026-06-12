---
title: "VIM syntax enable doesn't work in Edgy"
date: 2006-10-26
forum: General Help
---

### Post by branchus on 2006-10-26
Hello

I always write 'syntax enable' in .vimrc file, and it works fine for times. However, after I upgrade to Edgy Server edition, I couldn't use this command in VIM. it says 'E319: Sorry, the command is not available in this version'.

I just wonder, how can I make it work?

Thanks in advance

---

### Post by bsussman on 2006-10-26
Funny - doesn't seem to be working on my 6.06 desktop.

BUT

Works on my laptop which is 100% uptodate 6.10.

What version (:version in vim)?
mine is 7.0, patches 1-35 compiled 20 Oct 2006

---

### Post by garretwp on 2006-10-26
Edgy comes with a lite version of vim. You will need to do an apt-get for vim to get the full version. I had this problem when I first installed Edgy a few days ago.

- Garrett

---

### Post by branchus on 2006-10-26
> **bsussman said:**
> Funny - doesn't seem to be working on my 6.06 desktop.

BUT

Works on my laptop which is 100% uptodate 6.10.

What version (:version in vim)?
mine is 7.0, patches 1-35 compiled 20 Oct 2006

mine is the same as yours, but it doesn't work, anyone knows the reasons? (BTW: it works fine on my 6.06 server)

And my Edgy is a clean installation.

---

### Post by bsussman on 2006-10-26
Turns out my desktop problem is something in my .vimrc - the runtimepath had a previous version in it that did not exist.  I corrected and all is well.

So check your runtimepath in your .vimrc

---

### Post by branchus on 2006-10-26
> **bsussman said:**
> Turns out my desktop problem is something in my .vimrc

Have you tried renaming yours and manually turning on syntax?  Still not colorizing?

I've tried to turn it on manually, but the same error message turns out.

now I'm trying to get the full version, like garretwp said above

Thanks bros.

---

### Post by branchus on 2006-10-26
> **garretwp said:**
> Edgy comes with a lite version of vim. You will need to do an apt-get for vim to get the full version. I had this problem when I first installed Edgy a few days ago.

- Garrett

You are right. After I apt-get the full version of VIM, It works perfect now

Thanks all

---

### Post by nyinge on 2006-10-27
Does anyone experience incorrect key-mappings in the vim that comes with Edgy, such as pressing the "Back space" button would print out random alphabets in edit mode?

Also pressing left button would produce some garbage texts.

---

### Post by sandrovich on 2006-10-27
> **nyinge said:**
> Does anyone experience incorrect key-mappings in the vim that comes with Edgy, such as pressing the "Back space" button would print out random alphabets in edit mode?

Also pressing left button would produce some garbage texts.
You must update to the full version of vim. Edgy comes with a lite version.

---

### Post by gotgenes on 2006-10-27
I had the same question. Thanks very much for the replies! Now I can Vim happily. :)

---

### Post by sbassett on 2006-10-28
Thank GAWD!!!!! That little issue was driving me mad, and I love my vim!

---

### Post by aether on 2006-10-28
[http://ubuntuforums.org/showthread.php?t=286762&highlight=vim](http://ubuntuforums.org/showthread.php?t=286762&highlight=vim)

---

### Post by rbiswas on 2006-10-29
> **garretwp said:**
> Edgy comes with a lite version of vim. You will need to do an apt-get for vim to get the full version. I had this problem when I first installed Edgy a few days ago.

- Garrett
That fixed it! I would never have imagined that. Thanks

---

### Post by nyinge on 2006-10-31
> **sandrovich said:**
> You must update to the full version of vim. Edgy comes with a lite version.
Sorry for the late reply, but it's now working beautifully with the full version of vim.  Thanks!  :)

---

### Post by mahy on 2006-10-31
I don't quite understand. I did the upgrade to full version, it was only some 700 kB AND it was on the CD! WTH they couldn't've put it there by default?

---

### Post by wuhaa on 2006-11-06
> **garretwp said:**
> Edgy comes with a lite version of vim. You will need to do an apt-get for vim to get the full version. I had this problem when I first installed Edgy a few days ago.

- Garrett


Installing the full version works!! Thanks...

---

### Post by sonasi on 2007-01-17
Unbelievable!!!!  I have been pulling my hair out for days!!!  Why on earth would the FULL Vim not come by default????  Where would one even become informed of this fact if it were not for these forums??

Many thanks to you guys for posting the resolution.

---

### Post by h20Boodle on 2007-02-13
Installing vim-full did not work for me. Here's the problem as I see it.

(Go to bottom of this post to see how I fixed this.)

I run vim, which actually calls /usr/bin/vim.full
I open up vim by typing vim (or /usr/bin/vim.full) and I type ":set all". This shows my runtimepath set as follows:
runtimepath=~/.vim,/usr/share/vim/vimfiles,/usr/share/vim/vim64,
                           /usr/share/vim/vimfiles/after,~/.vim/after

That runtime path is wrong for the version of vim I have installed.(version 7.0.35, 1:7.0-035+1ubuntu5(edgy)) It should be set as I describe below.

I don't have any ~/.vim* entries, so I know I'm not setting the runtimepath elsewhere.

My "/etc/vim/vimrc" file should be getting referenced and then issuing this command:
runtime! debian.vim

I find debian.vim in /usr/share/vim/vim70/debian.vim, and it says the runtimepath is:
set runtimepath=~/.vim,/var/lib/vim/addons,/usr/share/vim/addons,
         /usr/share/vim/vimfiles,/usr/share/vim/vim70,/usr/share/vim/vimfiles/after,
        /usr/share/vim/addons/after,/var/lib/vim/addons/after,~/.vim/after

STOP!

I found the problem as I was writing this. I found that my VIMRUNTIME environment variable was being set in my .bashrc file.
export VIMRUNTIME=/usr/share/vim/vim64

I changed it to 
export VIMRUNTIME=/usr/share/vim/vim70

and now it sets the runtimepath correctly.

Phew!

---

