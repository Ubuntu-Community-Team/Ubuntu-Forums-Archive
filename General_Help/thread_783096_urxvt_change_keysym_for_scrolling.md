---
title: "urxvt: change keysym for scrolling"
date: 2008-05-05
forum: General Help
---

### Post by doc_solitude on 2008-05-05
Hello everybody!

Forgive me if this question turns out to be trivial after all, but I've been searching the internet for to long now! My problem is quite simple: I want to change the keyboard sequence that makes urxvt scroll up or down.
By default it is Shift+PageUp for scrolling up and Shift+PageDown for scrolling down. I'd prefer Shift+UpArrow and Shift+DownArrow. According to the urxvt man page I must set the keysym resource in my .Xdefaults.
It should then look something like this:

```
URxvt*keysym.Shift-Up: <command to scroll up>
URxvt*keysym.Shift-Down: <command to scroll down>
```

Unfortunately I can't find out with what I shall replace <command to scroll up> and <command to scroll down>. What are the commands that make urxvt scroll? I've done this for xterm before. It must be possible for urxvt, too! Somewhere I read urxvt would honour my xterm setting, but this is not the case.

Any help is appreciated!

Thanks in advance,

doc

---

### Post by Zed on 2008-11-20
So far as I can see, there isn't a good way to do it.

Your best bet would be to compile your own -- the changes would be to command.C and they're fairly obvious -- just changing the references to XK_Next and XK_Prior to XK_Down and XK_Up in one place.

You could bind the keys to a command to go up or down a fixed number of lines, insensitive to the size of the screen, e.g., 

```

URxvt.keysym.Shift-Up: command:\033]720;1\007
URxvt.keysym.Shift-Down: command:\033]721;1\007

```

makes it scroll up or down 1 line. This technique isn't very useful for whole pages, though.

And this is what I've done. Make sure you've installed rxvt-unicode-ml -- the ful package, with the built-in Perl interpreter. Then, in your .Xresources:

```

URxvt.keysym.Meta-Page_Up: perl:pageup
URxvt.keysym.Meta-Page_Down: perl:pagedown
URxvt.perl-lib: /usr/local/lib/urxvt/perl
URxvt.perl-ext: custom.pl

```

In /usr/local/lib/urxvt/perl/custom.pl (or wherever you specified above):

```

use List::Util qw(min max);

sub on_user_command {
  my ($term, $command) = @_;
  my $page_height = $term->nrow - 1;
  my $current_line = $term->view_start;
  my $new_line;
 for ($command) {
   /^pageup$/ and do {
     $new_line = max($current_line-$page_height, $term->top_row);
   };
   /^pagedown$/ and do {
     $new_line = min($current_line+$page_height, 0);
   };
 }
  $term->view_start($new_line);
  $term->want_refresh;
}

```

It's a little convoluted, but it actually works.

---

### Post by doc_solitude on 2008-11-24
Hello Zed,

many thanks for your reply. I had allready forgotten that I posted about this issue. In the meantime I switched back to xterm, as I could not find the answer anywhere else either. I will try your solution as soon as I find time to do so.

Thank you very much again!

Greetings

doc

---

