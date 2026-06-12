---
title: "Printf format is too long for type `belong' in description `version %ld, '"
date: 2017-02-07
forum: General Help
---

### Post by anonym777 on 2017-02-07
Hello, guys!

I am trying to extract the dd-wrt firmware image in order to modify it using firmware modification kit, but it fails and gives me the following error:

kea@ThinkPad-T43:~/Hentet/fmk$ ./extract-firmware.sh factory-to-ddwrt.bin /home/kea/extra/
Firmware Mod Kit (extract) 0.99, (c)2011-2013 Craig Heffner, Jeremy Collake

Preparing tools ...
bff_huffman_decompress.c: In function ‘unpack_parse_header’:
bff_huffman_decompress.c:167:14: warning: implicit declaration of function ‘read’ [-Wimplicit-function-declaration]
  bytesread = read(in, hdr + prelen, PACK_HEADER_LENGTH - prelen);
              ^
bff_huffman_decompress.c: In function ‘unpack’:
bff_huffman_decompress.c:318:22: warning: implicit declaration of function ‘dup’ [-Wimplicit-function-declaration]
  unpack_parse_header(dup(in), dup(out), pre, prelen, bytes_in, &unpackd);
                      ^
Scanning firmware...
/tmp/tmpUdutv8, 568: Warning: Printf format is too long for type `belong' in description `version %ld, '
/tmp/tmpUdutv8, 645: Warning: Printf format is too long for type `lelong' in description `size %lu'
/tmp/tmpUdutv8, 650: Warning: Printf format is too long for type `lelong' in description `edition %lu,'
/tmp/tmpUdutv8, 652: Warning: Printf format is too long for type `lelong' in description `%lu blocks,'
/tmp/tmpUdutv8, 654: Warning: Printf format is too long for type `lelong' in description `%lu files'
/tmp/tmpUdutv8, 655: Warning: Printf format is too long for type `lelong' in description `{jump-to-offset:%lu}'
/tmp/tmpUdutv8, 656: Warning: Printf format is too long for type `lelong' in description `{file-size:%lu}'
/tmp/tmpUdutv8, 660: Warning: Printf format is too long for type `belong' in description `size %lu'
/tmp/tmpUdutv8, 665: Warning: Printf format is too long for type `belong' in description `edition %lu,'
/tmp/tmpUdutv8, 667: Warning: Printf format is too long for type `belong' in description `%lu blocks,'
/tmp/tmpUdutv8, 669: Warning: Printf format is too long for type `belong' in description `%lu files'
/tmp/tmpUdutv8, 670: Warning: Printf format is too long for type `belong' in description `{jump-to-offset:%lu}'
/tmp/tmpUdutv8, 671: Warning: Printf format is too long for type `belong' in description `{file-size:%lu}'
/tmp/tmpUdutv8, 1387: Warning: Printf format is too long for type `belong' in description `, %ld x'
/tmp/tmpUdutv8, 1388: Warning: Printf format is too long for type `belong' in description `%ld,'
/tmp/tmpUdutv8, 1403: Warning: Printf format is too long for type `leshort' in description `%hd x'
/tmp/tmpUdutv8, 1404: Warning: Printf format is too long for type `leshort' in description `%hd'

Scan Time:     2017-02-07 13:31:19
Signatures:    193
Target File:   /home/kea/Hentet/fmk/factory-to-ddwrt.bin
MD5 Checksum:  b84548278a93e7be497b1f039e008d22

DECIMAL       HEX           DESCRIPTION
-------------------------------------------------------------------------------------------------------

Extracting 0 bytes of  header image at offset 0
ERROR: No supported file system found! Aborting...


I guess the problem comes from this that the Printf format is too long. Can somebody explain me what does it mean and how to fix it?

Thank you!

---

