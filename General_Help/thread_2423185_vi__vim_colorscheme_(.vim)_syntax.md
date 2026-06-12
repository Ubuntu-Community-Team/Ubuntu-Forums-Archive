---
title: "vi / vim colorscheme (.vim) syntax?"
date: 2019-07-18
forum: General Help
---

### Post by macbreak on 2019-07-18
Hello. 

I wonder, does anyone know of any resources which document how to design & create custom .vim color scheme files, as invoked by  :colorscheme <scheme name> ?

Google is as useless as ever. 

Thanks. :)

---

### Post by norobro on 2019-07-18
I feel your pain. I couldn't find good direction either and ended up with a scheme that I like by trial and error.

If you haven't already, install the package vim-runtime. That package contains 18 color config files in /usr/share/vim/vim81/colors. (e.g. blue.vim) 
Copy/rename one of the files to ~/.vim/colors/```
$ sudo apt install vim-runtime
$ mkdir -p ~/.vim/colors
$ cp /usr/share/vim/vim81/colors/blue.vim ~/.vim/colors/mycolors.vim
```Now you can edit the colors in mycolors.vim until you get a scheme that you like.

In case you don't know, you can see all of the colors set by a scheme with the command  > :highlight  
Good info in the docs: [https://vimhelp.org/syntax.txt.html#%3Ahighlight](https://vimhelp.org/syntax.txt.html#%3Ahighlight)

Also, there are a lot of color schemes available here: [https://vimcolors.com/](https://vimcolors.com/)

---

### Post by macbreak on 2019-07-19
> **norobro said:**
> I feel your pain. I couldn't find good direction either and ended up with a scheme that I like by trial and error.

If you haven't already, install the package vim-runtime. That package contains 18 color config files in /usr/share/vim/vim81/colors. (e.g. blue.vim) 
Copy/rename one of the files to ~/.vim/colors/```
$ sudo apt install vim-runtime
$ mkdir -p ~/.vim/colors
$ cp /usr/share/vim/vim81/colors/blue.vim ~/.vim/colors/mycolors.vim
```Now you can edit the colors in mycolors.vim until you get a scheme that you like.

In case you don't know, you can see all of the colors set by a scheme with the command  
Good info in the docs: [https://vimhelp.org/syntax.txt.html#%3Ahighlight](https://vimhelp.org/syntax.txt.html#%3Ahighlight)

Also, there are a lot of color schemes available here: [https://vimcolors.com/](https://vimcolors.com/)

Thank you ever so much for your helpfulness, and God bless you! :)

Regards.

---

