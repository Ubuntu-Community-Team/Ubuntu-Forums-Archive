---
title: "Codeblocks / gtk+"
date: 2013-01-24
forum: General Help
---

### Post by Noble Bell on 2013-01-24
I would like to start developing using codeblocks ide and gtk+ 3 toolkit. I have this setup in Windows and it has worked great. I want to get it setup to work properly on Ubuntu and am having trouble.

Could someone please offer some advice or point me in the right direction? I have tried to unpack the gtk+-3.6.4 archive and place it in /opt. I then created a simple project in codeblocks and when I try and compile it I get an error telling me that <gtk/gtk.h> cannot be found.

Thanks in advance.

---

### Post by Impavidus on 2013-01-25
No need to install anything manually, just install **libgtk-3-dev** from the repo's.  It includes the library and the header files.

---

### Post by Noble Bell on 2013-01-25
Thank you. I gave it a shot but it said it was already installed. So, I re-installed it. 

Tried the example code again in codeblocks and it gave the same error message.

I am wondering if I need to create a global variable in codeblocks pointing to the folder where this is installed?  

How might I find out where this library got installed?

The code is the code created by the codeblocks template for a gtk+ project:

```

#include <stdlib.h>
#include <gtk/gtk.h>

static void helloWorld (GtkWidget *wid, GtkWidget *win)
{
  GtkWidget *dialog = NULL;

  dialog = gtk_message_dialog_new (GTK_WINDOW (win), GTK_DIALOG_MODAL, GTK_MESSAGE_INFO, GTK_BUTTONS_CLOSE, "Hello World!");
  gtk_window_set_position (GTK_WINDOW (dialog), GTK_WIN_POS_CENTER);
  gtk_dialog_run (GTK_DIALOG (dialog));
  gtk_widget_destroy (dialog);
}

int main (int argc, char *argv[])
{
  GtkWidget *button = NULL;
  GtkWidget *win = NULL;
  GtkWidget *vbox = NULL;

  /* Initialize GTK+ */
  g_log_set_handler ("Gtk", G_LOG_LEVEL_WARNING, (GLogFunc) gtk_false, NULL);
  gtk_init (&argc, &argv);
  g_log_set_handler ("Gtk", G_LOG_LEVEL_WARNING, g_log_default_handler, NULL);

  /* Create the main window */
  win = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_container_set_border_width (GTK_CONTAINER (win), 8);
  gtk_window_set_title (GTK_WINDOW (win), "Hello World");
  gtk_window_set_position (GTK_WINDOW (win), GTK_WIN_POS_CENTER);
  gtk_widget_realize (win);
  g_signal_connect (win, "destroy", gtk_main_quit, NULL);

  /* Create a vertical box with buttons */
  vbox = gtk_vbox_new (TRUE, 6);
  gtk_container_add (GTK_CONTAINER (win), vbox);

  button = gtk_button_new_from_stock (GTK_STOCK_DIALOG_INFO);
  g_signal_connect (G_OBJECT (button), "clicked", G_CALLBACK (helloWorld), (gpointer) win);
  gtk_box_pack_start (GTK_BOX (vbox), button, TRUE, TRUE, 0);

  button = gtk_button_new_from_stock (GTK_STOCK_CLOSE);
  g_signal_connect (button, "clicked", gtk_main_quit, NULL);
  gtk_box_pack_start (GTK_BOX (vbox), button, TRUE, TRUE, 0);

  /* Enter the main loop */
  gtk_widget_show_all (win);
  gtk_main ();
  return 0;
}

```

Thanks in advance
NB

---

### Post by steeldriver on 2013-01-25
I don't use code::blocks but you probably need to set include / lib paths using pkg-config

[http://stackoverflow.com/questions/5921460/how-to-setup-gtk-to-develop-with-codeblocks-on-ubuntu-linux](http://stackoverflow.com/questions/5921460/how-to-setup-gtk-to-develop-with-codeblocks-on-ubuntu-linux)

---

### Post by Impavidus on 2013-01-25
Yes, you need to set some include path. You can do this manually (gcc -I/usr/include/gtk-3.0 et cetera), but I found there are quite a lot of them, so better use pkg-config. Google should be able to tell you how to use it. I'm a bit of a lower level programmer (mostly using text interfaces) not used to seven levels of dependencies, so I'd have to look it up myself too.

Edit: Since you're using an IDE, there must be a way to set those directories with include files there. It's mostly about /usr/include/{gtk-3.0,glib-2.0} and the like.

---

### Post by Noble Bell on 2013-01-26
> **steeldriver said:**
> I don't use code::blocks but you probably need to set include / lib paths using pkg-config

[http://stackoverflow.com/questions/5921460/how-to-setup-gtk-to-develop-with-codeblocks-on-ubuntu-linux](http://stackoverflow.com/questions/5921460/how-to-setup-gtk-to-develop-with-codeblocks-on-ubuntu-linux)

This did the trick. Thank you very much.

---

