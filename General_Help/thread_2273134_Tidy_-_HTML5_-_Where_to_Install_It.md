---
title: "Tidy - HTML5 - Where to Install It?"
date: 2015-04-10
forum: General Help
---

### Post by xExekut3x on 2015-04-10
So Tidy with HTML5 support must be built from source. The documentation is clear enough, except where to install it.

git clone [https://github.com/htacg/tidy-html5](https://github.com/htacg/tidy-html5)
cd tidy-html5/build/cmake
cmake ../.. [-DCMAKE_INSTALL_PREFIX=/path/for/install] <-- THIS PART
cmake --build . --config Release
make
sudo make install

Where should I put it? And how do I make it so it's recognized from the terminal?

---

### Post by grahammechanical on 2015-04-10
This gives you a clue

> cd tidy-html5/build/cmake

The git clone command will download the software and put it into a directory called tidy-html5/build/cmake.

The second command changes the directory to /tidy-html5/build/cmake

From where you run the third, fourth, fifth and sixth commands.

That is how I see this working.

Regards.

---

### Post by xExekut3x on 2015-04-10
I guess I didn't make myself clear.

For "[COLOR=#000000]/path/for/install": What should be put instead of that? And then, once you put whatever path you choose, how do you link so terminal can read it.[/COLOR]

---

### Post by Holger_Gehrke on 2015-04-11
The normal path for self compiled software is the '/usr/local/' hierarchy. Most build-systems use that by default if you don't configure them differently. The 'bin' directory in there is already part of $PATH and is searched before most of everything else and the same goes for '/usr/local/sbin'

---

### Post by andrew.46 on 2015-04-11
Perhaps consider using checkinstall?

---

