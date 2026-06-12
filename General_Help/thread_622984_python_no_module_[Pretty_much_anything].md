---
title: "python: no module [Pretty much anything]"
date: 2007-11-25
forum: General Help
---

### Post by hailtothethief on 2007-11-25
I've been banging my head against a wall for about two weeks now.
When ever I run a python file, I almost always get the following error thrown:

```
Traceback (most recent call last):
  File "new.py", line 1, in ?
    import Numeric
ImportError: No module named Numeric

```

Which, as I understand, is a fairly low-level library.
I know it's installed on my system:
```

bryan@bryan-laptop:~/Desktop$ locate python*numeric -i | grep -v Numeric/
/var/lib/dpkg/info/python-numeric.list
/var/lib/dpkg/info/python-numeric.md5sums
/var/lib/dpkg/info/python-numeric.postinst
/var/lib/dpkg/info/python-numeric.prerm
/usr/include/python2.4/Numeric
/usr/include/python2.5/Numeric
/usr/lib/python2.4/site-packages/Numeric
/usr/lib/python2.4/site-packages/Numeric.pth
/usr/lib/python2.5/site-packages/Numeric
/usr/lib/python2.5/site-packages/Numeric.pth
/usr/share/doc/python-numeric
/usr/share/doc/python-numeric/README
/usr/share/doc/python-numeric/changelog.Debian.gz
/usr/share/doc/python-numeric/changelog.gz
/usr/share/doc/python-numeric/copyright
/usr/share/pycentral/python-numeric
/usr/share/pycentral/python-numeric/site-packages
/usr/share/pycentral/python-numeric/site-packages/Numeric
/usr/share/pycentral/python-numeric/site-packages/Numeric.pth

```

I suspect it has something to do with my lib-dynload installation
I have three lib-dynload directories on my machine, which might be an issue:
```

/usr/lib/python2.4/lib-dynload:
array.so       _codecs_iso2022.so  _curses_panel.so  _heapq.so         _multibytecodec.so  resource.so  termios.so
audioop.so     _codecs_jp.so       _curses.so        _hotshot.so       nis.so              rgbimg.so    _testcapi.so
binascii.so    _codecs_kr.so       datetime.so       imageop.so        operator.so         select.so    time.so
_bisect.so     _codecs_tw.so       dbm.so            itertools.so      ossaudiodev.so      sha.so       timing.so
_bsddb.so      collections.so      dl.so             linuxaudiodev.so  parser.so           _socket.so   _tkinter.so
bz2.so         cPickle.so          fcntl.so          _locale.so        pyexpat.so          _ssl.so      unicodedata.so
cmath.so       crypt.so            fpectl.so         math.so           _random.so          strop.so     _weakref.so
_codecs_cn.so  cStringIO.so        gdbm.so           md5.so            readline.so         struct.so    zlib.so
_codecs_hk.so  _csv.so             grp.so            mmap.so           regex.so            syslog.so

```
```

/usr/lib/python2.5/lib-dynload:
array.so            _codecs_tw.so     dl.so            linuxaudiodev.so           _random.so   termios.so
audioop.so          collections.so    _elementtree.so  _locale.so                 readline.so  _testcapi.so
binascii.so         cPickle.so        fcntl.so         _lsprof.so                 resource.so  time.so
_bisect.so          crypt.so          fpectl.so        math.so                    rgbimg.so    _tkinter.so
_bsddb.so           cStringIO.so      _functools.so    mmap.so                    select.so    unicodedata.so
bz2.so              _csv.so           gdbm.so          _multibytecodec.so         _socket.so   _weakref.so
cmath.so            _ctypes.so        grp.so           nis.so                     spwd.so      zlib.so
_codecs_cn.so       _ctypes_test.so   _hashlib.so      operator.so                _sqlite3.so
_codecs_hk.so       _curses_panel.so  _heapq.so        ossaudiodev.so             _ssl.so
_codecs_iso2022.so  _curses.so        _hotshot.so      parser.so                  strop.so
_codecs_jp.so       datetime.so       imageop.so       pyexpat.so                 _struct.so
_codecs_kr.so       dbm.so            itertools.so     Python-2.5-py2.5.egg-info  syslog.so

```
```

/usr/local/lib/python2.5/lib-dynload:
array.so            _codecs_tw.so     datetime.so      linuxaudiodev.so    parser.so                    _socket.so
audioop.so          collections.so    dl.so            _locale.so          pyexpat.so                   spwd.so
binascii.so         cPickle.so        _elementtree.so  _lsprof.so          Python-2.5.1-py2.5.egg-info  strop.so
_bisect.so          crypt.so          fcntl.so         math.so             _random.so                   _struct.so
cmath.so            cStringIO.so      _functools.so    _md5.so             resource.so                  syslog.so
_codecs_cn.so       _csv.so           grp.so           mmap.so             rgbimg.so                    termios.so
_codecs_hk.so       _ctypes.so        _heapq.so        _multibytecodec.so  select.so                    _testcapi.so
_codecs_iso2022.so  _ctypes_test.so   _hotshot.so      nis.so              _sha256.so                   time.so
_codecs_jp.so       _curses_panel.so  imageop.so       operator.so         _sha512.so                   unicodedata.so
_codecs_kr.so       _curses.so        itertools.so     ossaudiodev.so      _sha.so                      _weakref.so

```

And finally, here are my sys.prefix and sys.path:

```
>>> import sys
>>> print sys.prefix
/usr/lib
>>> print sys.path
['', '/', '/usr/lib/lib/python24.zip', '/usr/lib/lib/python2.4', '/usr/lib/lib/python2.4/plat-linux2', '/usr/lib/lib/python2.4/lib-tk', '/usr/lib/python2.5', '/usr/local/lib/python2.5', '/usr/lib/python2.4', '/usr/local/lib/python2.4', '/usr/local/lib/python2.5/lib-dynload', '/usr/local/lib/python2.4/lib-dynload', '/usr/share/lib/python2.4/lib-dynload']
```

Of course, I could be completely off. If anyone could offer any help, it would be amazing.

---

### Post by dbbolton on 2008-06-02
> **hailtothethief said:**
> I've been banging my head against a wall for about two weeks now.
When ever I run a python file, I almost always get the following error thrown:

```
Traceback (most recent call last):
  File "new.py", line 1, in ?
    import Numeric
ImportError: No module named Numeric

```

Which, as I understand, is a fairly low-level library.
I know it's installed on my system:
```

bryan@bryan-laptop:~/Desktop$ locate python*numeric -i | grep -v Numeric/
/var/lib/dpkg/info/python-numeric.list
/var/lib/dpkg/info/python-numeric.md5sums
/var/lib/dpkg/info/python-numeric.postinst
/var/lib/dpkg/info/python-numeric.prerm
/usr/include/python2.4/Numeric
/usr/include/python2.5/Numeric
/usr/lib/python2.4/site-packages/Numeric
/usr/lib/python2.4/site-packages/Numeric.pth
/usr/lib/python2.5/site-packages/Numeric
/usr/lib/python2.5/site-packages/Numeric.pth
/usr/share/doc/python-numeric
/usr/share/doc/python-numeric/README
/usr/share/doc/python-numeric/changelog.Debian.gz
/usr/share/doc/python-numeric/changelog.gz
/usr/share/doc/python-numeric/copyright
/usr/share/pycentral/python-numeric
/usr/share/pycentral/python-numeric/site-packages
/usr/share/pycentral/python-numeric/site-packages/Numeric
/usr/share/pycentral/python-numeric/site-packages/Numeric.pth

```

I suspect it has something to do with my lib-dynload installation
I have three lib-dynload directories on my machine, which might be an issue:
```

/usr/lib/python2.4/lib-dynload:
array.so       _codecs_iso2022.so  _curses_panel.so  _heapq.so         _multibytecodec.so  resource.so  termios.so
audioop.so     _codecs_jp.so       _curses.so        _hotshot.so       nis.so              rgbimg.so    _testcapi.so
binascii.so    _codecs_kr.so       datetime.so       imageop.so        operator.so         select.so    time.so
_bisect.so     _codecs_tw.so       dbm.so            itertools.so      ossaudiodev.so      sha.so       timing.so
_bsddb.so      collections.so      dl.so             linuxaudiodev.so  parser.so           _socket.so   _tkinter.so
bz2.so         cPickle.so          fcntl.so          _locale.so        pyexpat.so          _ssl.so      unicodedata.so
cmath.so       crypt.so            fpectl.so         math.so           _random.so          strop.so     _weakref.so
_codecs_cn.so  cStringIO.so        gdbm.so           md5.so            readline.so         struct.so    zlib.so
_codecs_hk.so  _csv.so             grp.so            mmap.so           regex.so            syslog.so

```
```

/usr/lib/python2.5/lib-dynload:
array.so            _codecs_tw.so     dl.so            linuxaudiodev.so           _random.so   termios.so
audioop.so          collections.so    _elementtree.so  _locale.so                 readline.so  _testcapi.so
binascii.so         cPickle.so        fcntl.so         _lsprof.so                 resource.so  time.so
_bisect.so          crypt.so          fpectl.so        math.so                    rgbimg.so    _tkinter.so
_bsddb.so           cStringIO.so      _functools.so    mmap.so                    select.so    unicodedata.so
bz2.so              _csv.so           gdbm.so          _multibytecodec.so         _socket.so   _weakref.so
cmath.so            _ctypes.so        grp.so           nis.so                     spwd.so      zlib.so
_codecs_cn.so       _ctypes_test.so   _hashlib.so      operator.so                _sqlite3.so
_codecs_hk.so       _curses_panel.so  _heapq.so        ossaudiodev.so             _ssl.so
_codecs_iso2022.so  _curses.so        _hotshot.so      parser.so                  strop.so
_codecs_jp.so       datetime.so       imageop.so       pyexpat.so                 _struct.so
_codecs_kr.so       dbm.so            itertools.so     Python-2.5-py2.5.egg-info  syslog.so

```
```

/usr/local/lib/python2.5/lib-dynload:
array.so            _codecs_tw.so     datetime.so      linuxaudiodev.so    parser.so                    _socket.so
audioop.so          collections.so    dl.so            _locale.so          pyexpat.so                   spwd.so
binascii.so         cPickle.so        _elementtree.so  _lsprof.so          Python-2.5.1-py2.5.egg-info  strop.so
_bisect.so          crypt.so          fcntl.so         math.so             _random.so                   _struct.so
cmath.so            cStringIO.so      _functools.so    _md5.so             resource.so                  syslog.so
_codecs_cn.so       _csv.so           grp.so           mmap.so             rgbimg.so                    termios.so
_codecs_hk.so       _ctypes.so        _heapq.so        _multibytecodec.so  select.so                    _testcapi.so
_codecs_iso2022.so  _ctypes_test.so   _hotshot.so      nis.so              _sha256.so                   time.so
_codecs_jp.so       _curses_panel.so  imageop.so       operator.so         _sha512.so                   unicodedata.so
_codecs_kr.so       _curses.so        itertools.so     ossaudiodev.so      _sha.so                      _weakref.so

```

And finally, here are my sys.prefix and sys.path:

```
>>> import sys
>>> print sys.prefix
/usr/lib
>>> print sys.path
['', '/', '/usr/lib/lib/python24.zip', '/usr/lib/lib/python2.4', '/usr/lib/lib/python2.4/plat-linux2', '/usr/lib/lib/python2.4/lib-tk', '/usr/lib/python2.5', '/usr/local/lib/python2.5', '/usr/lib/python2.4', '/usr/local/lib/python2.4', '/usr/local/lib/python2.5/lib-dynload', '/usr/local/lib/python2.4/lib-dynload', '/usr/share/lib/python2.4/lib-dynload']
```

Of course, I could be completely off. If anyone could offer any help, it would be amazing.
I'm having the same issue. :(

---

