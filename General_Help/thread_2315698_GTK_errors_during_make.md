---
title: "GTK errors during make"
date: 2016-03-01
forum: General Help
---

### Post by silvio9 on 2016-03-01
Hi guys, I'm trying to use the gtk library to create a window. I need to use it with portaudio as well, after some research this is the result of the makefile:
```

CFILES := $(wildcard *.c)
OBJS := $(patsubst %.c,objs/%.o,$(CFILES))
HEADERS := $(wildcard *.h)

CFLAGS += -O2 -Wall -Werror -std=c99 -D_XOPEN_SOURCE
CFLAGS += $(shell pkg-config portaudio-2.0 --cflags)
CFLAGS += $(shell pkg-config --libs --cflags gtk+-2.0)
LIBS += $(shell pkg-config portaudio-2.0 --libs-only-l)
LDFLAGS += $(shell pkg-config portaudio-2.0 --libs-only-L --libs-only-other)

all: tuner

tuner: $(OBJS)
    $(CC) $(LDFLAGS) -o $@ $(OBJS) $(LIBS) 

objs:
    mkdir objs

objs/%.o: %.c $(HEADERS) | objs
    $(CC) $(CFLAGS) -c -o $@ $<

clean:
    -rm tuner
    -rm -r objs

```
I assume it is wrong because when I try to compile it these are the errors i get:

```

cc   -o tuner objs/libfft.o objs/main.o -lportaudio -lasound -lm -lpthread   
objs/main.o: In function `main':
main.c:(.text.startup+0x15): undefined reference to `gtk_init'
main.c:(.text.startup+0x1c): undefined reference to `gtk_window_new'
main.c:(.text.startup+0x24): undefined reference to `gtk_widget_show'
main.c:(.text.startup+0x29): undefined reference to `gtk_main'
collect2: error: ld returned 1 exit status
make: *** [tuner] Error 1

```
Anyone can help please?
thank you

---

### Post by steeldriver on 2016-03-01
Have you tried splitting 

```

CFLAGS += $(shell pkg-config --libs --cflags gtk+-2.0)

```

into

```

CFLAGS += $(shell pkg-config --cflags gtk+-2.0)

```

and

```

LIBS += $(shell pkg-config --libs gtk+-2.0)

```

? The way you're doing it at the moment, the gtk libraries are being added to your compile rule (where they aren't needed) but not to your link rule (where they are).

---

### Post by silvio9 on 2016-03-01
it works! thank you very much for our help, I went mad the whole evening trying to understand it!thanks again

---

