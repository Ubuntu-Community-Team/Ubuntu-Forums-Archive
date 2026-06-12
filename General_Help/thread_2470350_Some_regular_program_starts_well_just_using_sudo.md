---
title: "Some regular program starts well just using sudo"
date: 2021-12-27
forum: General Help
---

### Post by tommaso81 on 2021-12-27
I have recently installed Ubuntu 20.04.3 and Cinnamon enviroment. Under 20.04.0 I had no issue.

This is the problem:
when I launch applications like lazarus 2.0.12, or Openprog (from here: [http://openprog.altervista.org/OP_eng.html](http://openprog.altervista.org/OP_eng.html)) they hangs for at least 20 seconds at boot. Lazarus is an ide compiler, and compiled programs with it hang on closing them.

If I use sudo commands, there is no problem, everything goes well.

I tried to detect where the problem acting on openprog source code. I discovered that it hangs on this line:
```

    label = gtk_label_new(strings[I_Data]);    //"Data"
    data_scroll = gtk_scrolled_window_new(NULL,NULL);
    data = gtk_text_view_new();
    dataBuf = gtk_text_view_get_buffer(GTK_TEXT_VIEW(data));    
    gtk_text_view_set_editable(GTK_TEXT_VIEW(data),FALSE);

      //**************If  I put here "return 0;" the program doesn't hangs, without sudo also***************
    gtk_container_add(GTK_CONTAINER(data_scroll),data); <<-- HERE HANGS
      //**************If  I put here "return 0;" the program HANGS 20 seconds, if I use sudo it doesn't hang****************

    gtk_notebook_append_page(GTK_NOTEBOOK(notebook),data_scroll,label);
    font_desc = pango_font_description_from_string ("monospace 8");
    gtk_widget_modify_font (data, font_desc);
    pango_font_description_free (font_desc);

```

What could be ?

Thank you very much

---

### Post by vanadium on 2021-12-27
Temporarily create a new user, see if the issue happens there. Will show if this is an issue specific with your user account. Your issue actually might have been caused by running regular programs with "sudo".

---

### Post by tommaso81 on 2021-12-27
Just tried with new user. It doesn't make any difference. Which particular right is required by gtk_container_add function ?

---

### Post by tommaso81 on 2021-12-27
I think that the problem is due to GTK version. GTK2 applications have this issue, GTK3 do not. This is because from Lazarus if I compile with gtk2 the resulting program has this problem, if I compile with gtk3 don't.

Any help ?

Thank you

---

### Post by tommaso81 on 2021-12-31
Solved:

```

sudo apt-get install appmenu-gtk2-module

```

And add this line:
```

export GTK_MODULES=gail:atk-bridge:appmenu-gtk-module

```
to ~/.profile

---

