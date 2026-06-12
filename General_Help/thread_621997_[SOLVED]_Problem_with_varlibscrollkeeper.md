---
title: "[SOLVED] Problem with /var/lib/scrollkeeper"
date: 2007-11-24
forum: General Help
---

### Post by forestpixie on 2007-11-24
Sometimes when I install from the cli I get a long list of errors, all parser errors and to do with /var/lib/scrollkeeper.

Does anyone have any idea what might be causing it - installing from synaptic I get no errors. 

This time installing gnuplot caused it - sample below - I have no idea how many lines the error actually extends to the beginning gets cut off by terminal?

```
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2417: parser error : Opening and ending tag mismatch: tocsect1 line 2401 and doc
</toc></doc><doc docid="392"><doctitle>Manuel de l'applet Deskbar</doctitle><doc
            ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2458: parser error : Opening and ending tag mismatch: toc line 2394 and sect
</toc></doc></sect>
                   ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2615: parser error : Opening and ending tag mismatch: doc line 2394 and sect
    </sect>
           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5170: parser error : Opening and ending tag mismatch: sect line 2370 and ScrollKeeperContentsList
</ScrollKeeperContentsList>
                           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag sect line 1769

^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag ScrollKeeperContentsList line 2

^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : AttValue: " or ' expected
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : attributes construct error
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : Couldn't find end of Start Tag tocsect2 line 2402
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2417: parser error : Opening and ending tag mismatch: tocsect1 line 2401 and doc
</toc></doc><doc docid="392"><doctitle>Manuel de l'applet Deskbar</doctitle><doc
            ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2458: parser error : Opening and ending tag mismatch: toc line 2394 and sect
</toc></doc></sect>
                   ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2615: parser error : Opening and ending tag mismatch: doc line 2394 and sect
    </sect>
           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5170: parser error : Opening and ending tag mismatch: sect line 2370 and ScrollKeeperContentsList
</ScrollKeeperContentsList>
                           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag sect line 1769

^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag ScrollKeeperContentsList line 2

^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Unescaped '<' not allowed in attributes values
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : attributes construct error
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Couldn't find end of Start Tag tocsect3 line 3003
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4495: parser error : Extra content at the end of the document
ocid="199"><doctitle>Synaptic Manual</doctitle><docomf>/usr/share/omf/synaptic/s
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Unescaped '<' not allowed in attributes values
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : attributes construct error
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Couldn't find end of Start Tag tocsect3 line 3003
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4495: parser error : Extra content at the end of the document
ocid="199"><doctitle>Synaptic Manual</doctitle><docomf>/usr/share/omf/synaptic/s
^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : AttValue: " or ' expected
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : attributes construct error
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : Couldn't find end of Start Tag tocsect2 line 2402
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2417: parser error : Opening and ending tag mismatch: tocsect1 line 2401 and doc
</toc></doc><doc docid="392"><doctitle>Manuel de l'applet Deskbar</doctitle><doc
            ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2458: parser error : Opening and ending tag mismatch: toc line 2394 and sect
</toc></doc></sect>
                   ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2615: parser error : Opening and ending tag mismatch: doc line 2394 and sect
    </sect>
           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5170: parser error : Opening and ending tag mismatch: sect line 2370 and ScrollKeeperContentsList
</ScrollKeeperContentsList>
                           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag sect line 1769

^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag ScrollKeeperContentsList line 2

^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Unescaped '<' not allowed in attributes values
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : attributes construct error
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Couldn't find end of Start Tag tocsect3 line 3003
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4495: parser error : Extra content at the end of the document
ocid="199"><doctitle>Synaptic Manual</doctitle><docomf>/usr/share/omf/synaptic/s
^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : AttValue: " or ' expected
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : attributes construct error
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2402: parser error : Couldn't find end of Start Tag tocsect2 line 2402
<tocsect2 linkid=rce><docformat>text/xml</docformat><docseriesid>dc1bc4d4-40e7-1
                 ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2417: parser error : Opening and ending tag mismatch: tocsect1 line 2401 and doc
</toc></doc><doc docid="392"><doctitle>Manuel de l'applet Deskbar</doctitle><doc
            ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2458: parser error : Opening and ending tag mismatch: toc line 2394 and sect
</toc></doc></sect>
                   ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:2615: parser error : Opening and ending tag mismatch: doc line 2394 and sect
    </sect>
           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5170: parser error : Opening and ending tag mismatch: sect line 2370 and ScrollKeeperContentsList
</ScrollKeeperContentsList>
                           ^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag sect line 1769

^
/var/lib/scrollkeeper/fr/scrollkeeper_extended_cl.xml:5171: parser error : Premature end of data in tag ScrollKeeperContentsList line 2

^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Unescaped '<' not allowed in attributes values
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : attributes construct error
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3004: parser error : Couldn't find end of Start Tag tocsect3 line 3003
</tocsect2>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4495: parser error : Extra content at the end of the document
ocid="199"><doctitle>Synaptic Manual</doctitle><docomf>/usr/share/omf/synaptic/s
^

Setting up libgd-tools (2.0.34-1ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kevin@kevin-desktop:~$ 

```

---

### Post by Ehtetur on 2007-11-27
I think scrollkeeper has issues indexing on x64 OS.

Reinstall scrollkeeper and libscrollkeeper0... It will then take a very long time to reindex, but then you'll stop getting those error messages.

If anyone has a simpler solution, I'd really like to know about it.

---

### Post by forestpixie on 2007-11-28
ok thanks for that - I'm not running 64bit if that's what x64 is :)

I'll dig around the whole scrollkeeper thing though - thanks for the pointer

---

### Post by m10 on 2007-12-02
[this]("http://ubuntuforums.org/showthread.php?p=3693349") is a "duplicate thread" with a solution using *dpkg-reconfigure*

---

### Post by forestpixie on 2007-12-03
thanks for that - if I get no more occurences over the next couple days/weeks I'll mark thread :)

---

### Post by forestpixie on 2007-12-03
actually been busy today - no reoccurrence so that's that

thanks :)

---

