---
title: "vim noob needs help - multilingual spell check"
date: 2013-09-29
forum: General Help
---

### Post by GrouchyGaijin on 2013-09-29
Hi Guys,

I started trying to learn vim again and have made it further than I did before, but....

I need spell checking in both Swedish and English.

Following instructions I found at [http://ubuntu-se.org/phpBB3/viewtopic.php?f=67&t=32844](http://ubuntu-se.org/phpBB3/viewtopic.php?f=67&t=32844) I downloaded the Swedish language files:

sv.latin1.spl
sv.latin1.sug
sv.utf-8.spl
sv.utf-8.sug

I'm not sure if I need the latin or just utf so I grabbed both from:[ftp://ftp.vim.org/pub/vim/runtime/spell/](ftp://ftp.vim.org/pub/vim/runtime/spell/)

The instructions I found say:

[I][COLOR=#444444][FONT=Verdana]By default, Vim only installs spell files for the English language. To install spell files for your preferred language, download the *.spl and optionally, the *.sug files for your language and character encoding from [/FONT][/COLOR][ftp://ftp.vim.org/pub/vim/runtime/spell/](ftp://ftp.vim.org/pub/vim/runtime/spell/)[COLOR=#444444][FONT=Verdana] and save them to /usr/share/vim/vim72/spell/.[/FONT][/COLOR]

[COLOR=#444444][FONT=Verdana]To use these spell files, some configuration in /etc/vimrc is needed, e.g.:[/FONT][/COLOR]

[COLOR=#444444][FONT=Verdana]set spelllang=en,ru[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]set spell

[/FONT][/COLOR][/I][FONT=Verdana][COLOR=#444444]So I did that.  I copied the language files I downloaded to /usr/share/vim/vim73/spell/

I now have both English and Swedish spell checking in vim, which is cool, but I have a couple of questions.

1. When I type [/COLOR][/FONT]:set spelllang=sv,en I get an error that says
[COLOR=#ff0000]Error detected while processing /home/grouchygaijin/.vim/spell/sv.utf-8.spl:[/COLOR]
[COLOR=#ff0000]E763: Word characters differ between spell files
[/COLOR]
If I ignore this error and go about my text processing business, everything seems to work fine.  Vim catches and suggests words for misspellings in both languages.

Does anyone know how I can get rid of this error? It is a bit annoying.

2.  I'm typing :set spelllang=sv,en and :set spell each time I start vim.
Is there a way to have these commands launched automatically when vim starts?

---

### Post by Impavidus on 2013-09-29
1: No idea.

2: Create a .vimrc file. The file .vimrc will be a hidden file in your home directory (/home/username). In that file you can put the lines```
:set spelllang=sv,en
:set spell
```Commands put in .vimrc will be executed automatically when starting vim.

---

### Post by GrouchyGaijin on 2013-09-29
Thanks - I can live with the bogus error message since the spelling for both languages works.
Your tip of putting the commands in a .vimrc file is really convenient.

---

### Post by GrouchyGaijin on 2013-09-29
> **Impavidus said:**
> 1: No idea.
The solution was simple.  I replaced the existing English files with files
downloaded from vim.org.  The error is gone. 
:guitar:

---

