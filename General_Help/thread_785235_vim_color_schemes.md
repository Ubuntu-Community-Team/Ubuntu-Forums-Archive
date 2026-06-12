---
title: "vim color schemes"
date: 2008-05-07
forum: General Help
---

### Post by clef360 on 2008-05-07
Hi, I'm trying to get color schemes in vim to work. I've made a ~/.vim/colors/ folder and put some schemes in there. Then in my ~/.vimrc file i added the line:

colorscheme black

It doesn't return any errors when I open vim up, but there's no color scheme applied. Adding "syntax on" works fine, but I'd like to use some other color schemes. Thanks for your help in advance.

---

### Post by apoth on 2008-05-07
I have these two options added, not sure if either are any use for you, but I suspect one might be:

```
source /usr/share/vim/vim71/syntax/syntax.vim

colors koehler
```

---

### Post by clef360 on 2008-05-07
> **apoth said:**
> I have these two options added, not sure if either are any use for you, but I suspect one might be:

```
source /usr/share/vim/vim71/syntax/syntax.vim

colors koehler
```

Adding that "source" line sort of works, but the color schemes are not being displayed properly. The colors are wrong.

---

### Post by kerry_s on 2008-05-07
isn't that the wrong path?

/usr/share/vim/vim71/colors

there's a readme in there.

---

### Post by clef360 on 2008-05-07
> **kerry_s said:**
> isn't that the wrong path?

/usr/share/vim/vim71/colors

there's a readme in there.

If I add 

source /usr/share/vim/vim71/colors

to my .vimrc I get the following error message while starting up vim.

```
Cannot source a directory: "/usr/share/vim/vim71/colors"
Error detected while processing /home/dinyu/.vimrc:
line    5:
E484: Can't open file /usr/share/vim/vim71/colors

```

I checked the readme file in there and it was about how to write your own color scheme. I have an existing color scheme that I would like to make work. Thanks.

---

### Post by Ramses de Norre on 2008-05-07
In ~/.vimrc: **colorscheme custom** and save the colorscheme as ~/.vim/colors/custom.vim .

---

### Post by kerry_s on 2008-05-07
> **clef360 said:**
> If I add 

source /usr/share/vim/vim71/colors

to my .vimrc I get the following error message while starting up vim.

```
Cannot source a directory: "/usr/share/vim/vim71/colors"
Error detected while processing /home/dinyu/.vimrc:
line    5:
E484: Can't open file /usr/share/vim/vim71/colors

```

I checked the readme file in there and it was about how to write your own color scheme. I have an existing color scheme that I would like to make work. Thanks.


just, starting to mess with it now. you don't need to source anything. just put the theme.vim in ~/.vim/colors and just put the name in .vimrc.
example:
colorscheme theme

here's what mine looks like, i'm using 1 of the stock choices for now, still googling for a nice theme. :)

---

### Post by kerry_s on 2008-05-07
good place to find themes->
[http://www.vim.org/scripts/script_search_results.php?keywords=&script_type=color+scheme&order_by=creation_date&direction=descending&search=search](http://www.vim.org/scripts/script_search_results.php?keywords=&script_type=color+scheme&order_by=creation_date&direction=descending&search=search)

---

### Post by clef360 on 2008-05-07
It does kind of apply a color scheme when I do that, but the color and bolding doesn't match the examples shown here
[http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/index-c.html](http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/index-c.html)

Neither does it match the colors of any other scheme I download. Could it possibly be a setting in the terminal window preferences?

Here's my .vimrc in the upper right, what the colors look like in the lower right, and what it's supposed to look like on the left.

---

### Post by kerry_s on 2008-05-07
thanks for that link.

yeah, i see what your talking about, i'm sure there's probably other variables, could be anything from the type of terminal to the display resolution, maybe even the version of vim. 
your screen shot looked pretty close to me. i'm thinking maybe you need to add the number of colors to your vimrc, i noticed some themes say you need to add the 256 color setting and others are made for 8 or 16.

**set t_Co=256**

it doesn't work for me cause my vid card only does 16 color. when i use that setting i lose all highlighting. :(
also i'm using rxvt, not sure if it makes a difference.

anyways, i say just get a theme with the colors you like, don't worry about matching screen shots.
:lolflag:

---

### Post by clef360 on 2008-05-07
adding that line worked! thanks!

---

