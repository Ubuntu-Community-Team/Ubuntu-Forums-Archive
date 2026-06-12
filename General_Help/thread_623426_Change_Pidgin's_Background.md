---
title: "Change Pidgin's Background"
date: 2007-11-25
forum: General Help
---

### Post by 1337455 10534 on 2007-11-25
How do I change the background of Pidgin (only). I'm happy with my theme/Emerald/background, so.. I dont want to change that. How do I get Pidgin's background to, say, black?
I dont have a gtkrc-2.0 file and I don't know where I should create one since I compiled Pidgin for myself...
> 
As an example, you can put this into .gtkrc-2.0 to change the font size for all GTK+ applications:
```

# Sets the font used by all gtk applications.
gtk-font-name = "Verdana 9"

```
Alternatively, you can do this to change the font size for other elements:
```

# This is the style section.  You need this for the examples below.
# If you are going to copy the example, copy the entire block,
# including the "{" and "}" lines.
style "imhtml-fix"
{
    font_name = "Sans 10"
}

# This will apply the font style just shown to various components.
# If you are going to copy the example, copy the line that does
# what you want.

# Conversation entry box--where you type.
widget "*pidgin_conv_entry" style "imhtml-fix"

# Conversation history pane--where you read the conversation.
widget "*pidgin_conv_imhtml" style "imhtml-fix"

# Log viewer--where you read stored logs
widget "*pidgin_log_imhtml" style "imhtml-fix"

# formatting-capable entry areas (IMHtml widgets) in request dialogs
widget "*pidgin_request_imhtml" style "imhtml-fix"

# formatting-capable notification areas in dialogs (again, IMHtml widgets)
widget "*pidgin_notify_imhtml" style "imhtml-fix"

```
Background colors can be changed similarly, by finding the correct widget names and setting appropriate bg elements. Other widgets in Pidgin can be controlled in a similar manner. For example, to change the background color for a group, do something similar to the following:
```

style "NoPidginGroupColor"
{
    bg[ACTIVE]   = "#FFFFFF"
}

widget "*pidgin_blist_treeview" style "NoPidginGroupColor"

```


---

