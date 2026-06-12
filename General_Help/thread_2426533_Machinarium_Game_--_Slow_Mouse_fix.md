---
title: "Machinarium Game -- Slow Mouse fix"
date: 2019-09-10
forum: General Help
---

### Post by hackerb9 on 2019-09-10
As has been noted in a closed thread, the Flash version of the beautiful game [Machinarium]("https://www.humblebundle.com/store/machinarium-collectors-edition") does not play very well under Ubuntu. The main problem is that the mouse is extremely laggy, especially when the cursor changes to a different icon (for example, when trying to use an item). This makes the game frustrating and ultimately unplayable. 

There is a solution posted by Aaron Plattner, which is to recompile libX11 with a hack for the cursors. However, the instructions he gave no longer work quite right, mostly because machines nowadays are 64-bit. Here is a recipe which does work.

```

sudo apt install git gcc-multilib xtrans-dev libx11-dev:i386
git clone -b machinarium-workaround git://people.freedesktop.org/~aplattner/libX11
cd libX11
sed -i 's#$(srcdir)/##' nls/Makefile.am
CFLAGS=-m32 LDFLAGS=-m32 ./autogen.sh --prefix=$HOME/games/machinarium
make install
cd $HOME/games/machinarium
LD_LIBRARY_PATH=`pwd`/lib ./Machinarium
```

---

### Post by Dennis N on 2019-09-10
I found that if you play the game in window mode, not full screen, the mouse problem goes away.

---

