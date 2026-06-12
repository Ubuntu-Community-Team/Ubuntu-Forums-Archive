---
title: "pidgin background color"
date: 2008-05-17
forum: General Help
---

### Post by mathfeel on 2008-05-17
Hi, I am using a black theme. So it is extremely annoying that when I chat via pidgin, the msg other send me (usually in black) is completely invisible over a black background.

So I am trying set the background of the pidgin chat window. So I edited my /.purple/gtkrc-2.0:

```
style "purplerc_style"
{
  GtkIMHtml::hyperlink-color = "#00FF37"
  GtkIMHtml::send-name-color = "#AA000A"
  GtkIMHtml::receive-name-color = "#0AAA00"
  GtkIMHtml::background-color = "#FFFFFF"
}
widget_class "*" style "purplerc_style"

style "NoPidginGroupColor"
{
  bg[ACTIVE]   = "#FFFFFF"
}
#widget "*pidgin_blist_treeview" style "NoPidginGroupColor"
widget "*" style "NoPidginGroupColor"

```

No effect. Am I doing this right? Also, what is widget name for the chat window (not the buddy list).

---

### Post by m-m-me on 2008-10-08
Hi, same exact problem here, I have to change appearance settings every time(which throws everything else off) or highlight each new message



(English* is* my first language, BTW)

---

### Post by dunomous on 2009-04-01
Dunno if you ever got this figured out, but I'd like to know if you ever found a solution. My guess is that whichever gtk theme you're using may be overwriting the purple gtk file. You may be better off defining that in your theme's gtk file.

---

### Post by n3had on 2009-08-16
> **dunomous said:**
> Dunno if you ever got this figured out, but I'd like to know if you ever found a solution. My guess is that whichever gtk theme you're using may be overwriting the purple gtk file. You may be better off defining that in your theme's gtk file.

Tools-->plugins-->conversation colors

and click on received messages and change the color

hope it helps 

nehad

---

### Post by stoffe on 2009-12-24
Here's how I did it to better work with the theme from Ubuntu Satanic:

```
~/.purple$ cat gtkrc-2.0 
# Create a style called "satanic" where the text and base colors can be set:
style "satanic"
{
   base[NORMAL] = "#CCCCCC"
   text[NORMAL] = "#000000"
}

# Apply "satanic" to conversation entry box--where you type.
widget "*pidgin_conv_entry" style "satanic"

# Apply "satanic" to conversation history pane--where you read the conversation.
widget "*pidgin_conv_imhtml" style "satanic"

```

---

### Post by dunomous on 2009-12-25
> **stoffe said:**
> Here's how I did it to better work with the theme from Ubuntu Satanic:

```
~/.purple$ cat gtkrc-2.0 
# Create a style called "satanic" where the text and base colors can be set:
style "satanic"
{
   base[NORMAL] = "#CCCCCC"
   text[NORMAL] = "#000000"
}

# Apply "satanic" to conversation entry box--where you type.
widget "*pidgin_conv_entry" style "satanic"

# Apply "satanic" to conversation history pane--where you read the conversation.
widget "*pidgin_conv_imhtml" style "satanic"

```

Works great! Tank!

---

