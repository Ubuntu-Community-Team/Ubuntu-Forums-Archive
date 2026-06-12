---
title: "Can I get Vim help here?"
date: 2008-02-05
forum: General Help
---

### Post by MountainX on 2008-02-05
If this isn't the best place to ask this, please let me know.

Using Vim, I want to open the URL in the current line in my default browser in Ubuntu.

I found some excellent help here:
[http://www.vim.org/tips/tip.php?tip_id=306](http://www.vim.org/tips/tip.php?tip_id=306)
...but it is a bit Windows-centric and being a Linux newbie I need a few more details.

I need to know a couple things:
1. which 'config' file do I place this code in? (I'm using Cream, btw.)
2. how do I refer to my default browser under Ubuntu?
3. is the best URL regex this one? \%(http://\|www\.\)[^ ,;\t]*

I'm hoping I can make this smart enough to select the whole url if I just have the cursor on the line of text containing a valid url.

Here's the script from the link above:

let $PATH = $PATH . ';c:\Programs\FireFox1.5'
"=== evoke a web browser
function! Browser ()
    let line0 = getline (".")
    let line = matchstr (line0, "http[^ ]*")
    :if line==""
      let line = matchstr (line0, "ftp[^ ]*")
    :endif
    :if line==""
      let line = matchstr (line0, "file[^ ]*")
    :endif
    let line = escape (line, "#?&;|%")
    ":if line==""
    "  let line = "\"" . (expand("%:p")) . "\""
    ":endif
    exec ':silent !firefox.exe ' . "\"" . line . "\""
endfunction

map ,w :call Browser ()<CR>

----------------------------------------
also found some stuff here:
[http://www.google.com/codesearch?as_q=open+url+in+browser&as_lang=vim](http://www.google.com/codesearch?as_q=open+url+in+browser&as_lang=vim)

---

### Post by jrib on 2008-02-05
1.  You can drop it in your ~/.vimrc for vim. I believe Cream sources this by default as well.  It also has its own rc file whose location I do not know offhand
2. If you are in gnome, "gnome-open" will work
3. ?  The comments in your link have some suggestions though

---

### Post by MountainX on 2008-02-06
You were right - the best solution is to use Cream.

---

