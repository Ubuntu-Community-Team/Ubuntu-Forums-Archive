---
title: "trouble with thumb drives"
date: 2012-11-06
forum: General Help
---

### Post by princeofnam on 2012-11-06
I've tried transferring files to thumb drives on my Kubuntu several times now.  Each time and with each  thumb drive transfers will start with a fast write speed, then immediately slow down and stop completely, then start again with a fast write speed, only to slow down immediately again.  Does anyone understand why this might be happening?  It didn't always used to do this.

i also just received a bunch of random errors:

The crashed program seems to use third-party or local libraries:

/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/codecs/libqcncodecs.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libQtWebKit.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/imageformats/libqsvg.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/codecs/libqjpcodecs.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libqtjambi.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libcom_trolltech_qt_network.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/codecs/libqkrcodecs.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/imageformats/libqjpeg.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libQtCore.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libQtNetwork.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/imageformats/libqtiff.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libcom_trolltech_qt_core.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/codecs/libqtwcodecs.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libphonon.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/imageformats/libqmng.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libcom_trolltech_qt_gui.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libQtSvg.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libcom_trolltech_qt_xml.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libQtGui.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libQtXml.so.4
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/plugins/imageformats/libqgif.so
/tmp/QtJambi_sushi_amd64_4.5.2_01_gcc-20090628-2055/lib/libcom_trolltech_qt_webkit.so

It is highly recommended to check if the problem persists without those first.

Do you want to continue the report process anyway?

---

### Post by Zorael on 2012-11-09
How are you transferring the files? Dragging and dropping via the file manager?

When it does this, try opening up **KSysLog**. If memory serves there should be a **dmesg** tab/section; does it say anything about transfer errors there? It could simply be that your thumbdrive has some busted/worn out pages or cells.

(You can also get this output by entering **dmesg** in a terminal.)

---

