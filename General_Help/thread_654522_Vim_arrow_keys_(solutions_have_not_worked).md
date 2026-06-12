---
title: "Vim arrow keys (solutions have not worked)"
date: 2007-12-31
forum: General Help
---

### Post by Kache on 2007-12-31
Installing Ubuntu 7.10 Gutsy on Sony Vaio TZ130

I've searched all over the forums and the "sudo apt-get install vim-full" did not let me use the arrow keys the way I'd like. (Though it did let me apply the other settings like syntax highlighting.)

I've worked in Linux environments here and there, even though this is my first time installing Linux on a computer, and I've definitely used arrow keys in insert mode.

The same thing applies to the backspace, delete keys, and mouse scroll wheels in insert mode.

-K

---

### Post by der_joachim on 2008-01-01
How does your .vimrc look?

---

### Post by aJayRoo on 2008-01-01
Yeah the .vimrc file might be restricting you. I always start off with the example vimrc file and customise it to my taste.
```
cp /usr/share/vim/vim71/vimrc_example.vim ~/.vimrc
```
will copy the example file into your home directory (backup the one you have first of course). Hopefully this should fix your problem. Also make sure you start vim and not vi, as on some setups this starts vim in vi compatibility mode and the traditional keys are used.

---

### Post by Kache on 2008-01-01
Awesome. It looks like the vi compatibility was set on in /etc/vim/vimrc

Everything's working like I expect it now, thanks!

By the way, I read somewhere that .vimrc had been "depreciated" b/c sometimes it is changed when updates are done, so the best place to add your own settings is in /etc/vim/vimrc.

---

### Post by aJayRoo on 2008-01-01
I can't imagine that '~/.vimrc' would be deprecated, where did you read that? The purpose of the '~/.vimrc' file is to allow users that do not have administrative rights to be able to customise vim to their taste so I see no reason why it would ever be deprecated. If it was then many people (including myself) would have to use the system settings for vim when at work, which would be inconvenient to say the least! I know that changing the debian.vim file is a bad idea as that is overwritten on updates, perhaps that is what you are referring to? The is a list of files used by vim on the vim manpage, interestingly it does not mention '/etc/vim/vimrc' but I'm sure I have heard of other people placing their customisations there too.

---

### Post by Kache on 2008-01-07
oh, I see. I guess I read /etc/vim/vimrc wrong.

I suppose the "proper" place to put my customized vim settings would be in .vimrc in my home directory, since it's more of a user settings thing.

---

### Post by aJayRoo on 2008-01-07
Yeah, personally I prefer the settings to be stored in my home directory. My preference is based on the fact that I can reinstall my operating system without losing custom settings (as I have /home on its own partition).

---

