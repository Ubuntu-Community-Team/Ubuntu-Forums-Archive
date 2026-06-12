---
title: "[SOLVED] dcraw installation error"
date: 2007-08-21
forum: General Help
---

### Post by gobbles414 on 2007-08-21
Hi all,

I am trying to install dcraw using [the dcraw webpage]("http://cybercom.net/~dcoffin/dcraw"). I am not using the version in the repositories because version 8.39 does not work with my Olympus SLR. The current version, 8.77, should support my camera. Using the second installation method mentioned on the homepage, which I have used successfully in the past, I get a lot of errors. A sample follows:

```
joxer@joxer:~$ dcraw.c: In function ‘parse_rollei’:
dcraw.c:5599: warning: incompatible impl
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5338: error: storage size of ‘t’ isn’t known
dcraw.c:5623: error: ‘data_offset’ undeclared (first u
bash: dcraw.c:5338:: command not found
joxer@joxer:~$ dcraw.c:5340: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c: In function ‘foveon_gets’:
dcraw.c:5630: error: ‘ifp’joxer@joxer:~$ dcraw.c:5340: error: ‘SEEK_SET’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
 undeclared (first use in this function)
dcraw.c:5630: error: ‘SEEK_SET’joxer@joxer:~$ dcraw.c:5341: warning: incompatible implicit declaration of built-in function ‘memset’
 undeclared (first use in this function)
dcraw.c: In function ‘parse_foveon’:
dcraw.c:5bash: dcraw.c:5341:: command not found
joxer@joxer:~$ dcraw.c:5344: warning: incompatible implicit declaration of built-in function ‘
643: error: ‘ifp’ undeclared (first use in this function)
dcraw.c:5643: error:bash: dcraw.c:5344:: command not found
joxer@joxer:~$ dcraw.c:5347: warning: incompatible implicit declaration of built-in functi
 ‘SEEK_SET’ undeclared (first use in this function)
dcraw.c:5645: error:bash: dcraw.c:5347:: command not found
joxer@joxer:~$ dcraw.c:5349: warning: incompatible implicit declaration of built-in functi
 ‘SEEK_END’ undeclared (first use in this function)
dcraw.c:5659: error:bash: dcraw.c:5349:: command not found
joxer@joxer:~$ dcraw.c:5353: error: ‘thumb_offset’ undeclared (f
bash: syntax error near unexpected token `('
 ‘SEEK_CUR’ undeclared (first use in this function
joxer@joxer:~$ dcraw.c:5363: error: ‘data_offset’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:5665: error: ‘data_offset’ undeclared (first use in this function)
joxer@joxer:~$ dcraw.c:5367: error: ‘timestamp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:5669: error: ‘thumb_offset’ undeclared (first use in this functi
joxer@joxer:~$ dcraw.c:5368: warning: incompatible implicit declaration of built-in function ‘strcpy’
dcraw.c:5671: error: ‘write_thumb’ undeclared (first use in this function)
dcraw.c:567bash: dcraw.c:5368:: command not found
joxer@joxer:~$ dcraw.c:5370: error: ‘write_thumb’ undeclared (fir
bash: syntax error near unexpected token `('
1: error: ‘jpeg_thumb’ undeclared (first use in thi
joxer@joxer:~$ dcraw.c:5370: error: ‘rollei_thumb’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:5677: error: ‘foveon_thumb’ undeclared (first use in this function)
joxer@joxer:~$ dcraw.c: In function ‘parse_sinar_ia’:
dcraw.c:5681: error: ‘meta_offset’ und
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5379: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:5699: warning: incompatible implicit declaration of built-in f
joxer@joxer:~$ dcraw.c:5379: error: ‘SEEK_SET’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:5705: error: ‘timestamp’ undeclared (first use in this function
joxer@joxer:~$ dcraw.c:5385: error: ‘meta_offset’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c: In function ‘adobe_coeff’:
dcraw.c:6070: warning: incompatible imjoxer@joxer:~$ dcraw.c:5386: error: ‘thumb_offset’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
plicit declaration of built-in function ‘sprintf’
dcraw.c:6072: warning: incjoxer@joxer:~$ dcraw.c:5387: error: ‘data_offset’ undeclared (first use in this 
bash: syntax error near unexpected token `('
ompatible implicit declaration of built-in function ‘strlen’
dcrawjoxer@joxer:~$ dcraw.c:5392: warning: incompatible implicit declaration of built-in f
.c: In function ‘guess_byte_order’:
dcraw.c:6108: error: ‘ifp’ bash: dcraw.c:5392:: command not found
joxer@joxer:~$ dcraw.c:5393: warning: incompatible implicit declaration of built-in functi
undeclared (first use in this function)
dcraw.c: In function ‘identify’:bash: dcraw.c:5393:: command not found
joxer@joxer:~$ dcraw.c:5401: error: ‘write_thumb’ undeclared (first use in this function)
bash: syntax error near unexpected token `('

dcraw.c:6198: warning: incompatible implicit declaration of built-in function joxer@joxer:~$ dcraw.c:5401: error: ‘ppm_thumb’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
‘memset’
dcraw.c:6199: error: ‘thumb_offset’ undeclared (first use injoxer@joxer:~$ dcraw.c: In function ‘parse_phase_one’:
 this function)
dcraw.c:6201: error: ‘writbash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5411: warning: incompatible implicit declaration of built-in functio
e_thumb’ undeclared (first use in this function)
dcraw.c:6201: error: ‘jpbash: dcraw.c:5411:: command not found
joxer@joxer:~$ dcraw.c:5412: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
eg_thumb’ undeclared (first use in this function)
dcraw.c:6202: errorjoxer@joxer:~$ dcraw.c:5412: error: ‘SEEK_SET’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
: ‘data_offset’ undeclared (first use in this function)
dcraw.c:6204: erjoxer@joxer:~$ dcraw.c:5442: error: ‘data_offset’ und
ror: ‘timestamp’ undeclared (first use 
bash: dcraw.c:5442:: command not found
joxer@joxer:~$ dcraw.c:5443: error: ‘meta_offset’ undeclared (first use in this f
dcraw.c:6220: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5448: error: ‘strip_offset’ undeclared (first use in this funct
dcraw.c:6220: error: ‘SEEK_SET’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5455: warning: incompatible implicit declaration of built-in functi
dcraw.c:6222: error: ‘SEEK_END’ undeclared (first use in this function)
bash: dcraw.c:5455:: command not found
joxer@joxer:~$ dcraw.c:5462: warning: incompatible implicit declaration of built-in function ‘strcpy’
dcraw.c:6224: warning: passing argument 2 of ‘my_memmem’ makes pointer from integer wi
bash: dcraw.c:5462:: command not found
joxer@joxer:~$ dcraw.c: In function ‘parse_fuji’:
dcraw.c:6224: error: too many argument
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5476: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:6225: warning: passing argument 2 of ‘my_memmem’ makes poi
joxer@joxer:~$ dcraw.c:5476: error: ‘SEEK_SET’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:6225: error: too many arguments to function ‘my_memmem’
dcraw.cjoxer@joxer:~$ dcraw.c: In function ‘parse_jpeg’:
:6244: warning: incompatible implicit d
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5503: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:6251: warning: incompatible implicit declaration of built-in f
joxer@joxer:~$ dcraw.c:5503: error: ‘SEEK_SET’ undeclared (first use in this fun
bash: syntax error near unexpected token `('
dcraw.c:6254: warning: incompatible implicit declaration of built-in 
joxer@joxer:~$ dcraw.c: In function ‘parse_riff’:
dcraw.c:6257: warning: incompatible im
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5531: error: storage size of ‘t’ isn’t known
dcraw.c:6290: warning: incompatible implicit declaration o
bash: dcraw.c:5531:: command not found
joxer@joxer:~$ dcraw.c:5534: error: ‘ifp’ undeclared (first use in this function)
dcraw.c:6299: warning: incompatible implicit declaration of built-in f
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5544: warning: incompatible implicit declaration of built-in function ‘mem
dcraw.c:6300: warning: incompatible implicit declaration of built-in function ‘str
bash: dcraw.c:5544:: command not found
joxer@joxer:~$ dcraw.c:5545: warning: incompatible implicit declaration of built-in function ‘sscanf
dcraw.c:6303: warning: incompatible implicit declaration of built-in function ‘strlen
bash: dcraw.c:5545:: command not found
joxer@joxer:~$ dcraw.c:5551: error: ‘timestamp’ undeclared (first use in this fun
dcraw.c:6309: warning: incompatible implicit declaration of built-in f
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5554: error: ‘SEEK_CUR’ undeclared (first use in this function)
dcraw.c:6675: warning: incompatible implicit declaration of built-in functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c: In function ‘parse_smal’
dcraw.c:7072: error: ‘layer_thumb&#65533;&#65533;
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5561: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
dcraw.c:7198: warning: incompatible implicit declaration of built-in f
joxer@joxer:~$ dcraw.c:5561: error: ‘SEEK_SET’ un
dcraw.c:7212: warning: incompatible im
bash: dcraw.c:5561:: command not found
joxer@joxer:~$ dcraw.c:5565: error: ‘SEEK_CUR’ undeclared (first use in this func
bash: syntax error near unexpected token `('
dcraw.c:7212: error: ‘stderr’ undeclared (first use in this functi
joxer@joxer:~$ dcraw.c:5567: error: ‘data_offset’ undeclared (first use in this functi
bash: syntax error near unexpected token `('
dcraw.c: In function ‘convert_to_rgb’:
dcraw.c:7328: warning: incompatijoxer@joxer:~$ dcraw.c:5570: warning: incompatible implicit declaration of built-in function ‘strcpy’
ble implicit declaration of built-in function ‘memcpy’
dcraw.c:7332: warning: incompatibash: dcraw.c:5570:: command not found
joxer@joxer:~$ dcraw.c:5571: warning: incompatible implicit declaration of built-in functi
ble implicit declaration of built-in function ‘calloc’
dcraw.c:7343: warbash: dcraw.c:5571:: command not found
joxer@joxer:~$ dcraw.c: In function ‘parse_cine’:
ning: incompatible implicit declaration
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5581: error: ‘ifp’ undeclared (first use in this function)
dcraw.c:7362: warning: incompatible implicit declaration of built-in f
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5581: error: ‘SEEK_SET’ undeclared (first use in this function)
dcraw.c:7370: warning: incompatible implicit declaration of built-in functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5583: error: ‘SEEK_CUR’ undeclared (first use in this function)
dcraw.c:7370: error: ‘stderr’ undeclared (first use in this function)
dbash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5588: error: ‘timestamp’ undeclared (first use in this function)
craw.c:7373: warning: incompatible implicit declaration of built-in function 
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5598: warning: incompatible implicit declaration of built-in function ‘str
dcraw.c: In function ‘fuji_rotate’:
dcraw.c:7403: warning: incompatible implicitbash: dcraw.c:5598:: command not found
joxer@joxer:~$ dcraw.c:5599: warning: incompatible impl
 declaration of built-in function ‘fpri
bash: dcraw.c:5599:: command not found
joxer@joxer:~$ dcraw.c:5623: error: ‘data_offset’ undeclared (first u
dcraw.c:7403: error: ‘stderr’ undeclared (first use in
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c: In function ‘foveon_gets’:
dcraw.c:7405: warning: incompatible imp
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5630: error: ‘ifp’ undeclared (first use in this function)
dcraw.c:7408: warning: incompatible implicit declaration of built-in f
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5630: error: ‘SEEK_SET’ undeclared (first use in this function)
dcraw.c: In function ‘stretch’:
dcraw.c:7438: warning: incompatible impbash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c: In function ‘parse_foveon’:
licit declaration of built-in function &#65533;&#65533;
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:5643: error: ‘ifp’ undeclared (first use in this function)
dcraw.c:7438: error: ‘stderr’ undeclared (first use in this functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5643: error: ‘SEEK_SET’ undeclared (first use in this function)
dcraw.c:7441: warning: incompatible implicit declaration of built-in functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5645: error: ‘SEEK_END’ undeclared (first use in this function)
dcraw.c:7453: warning: incompatible implicit declaration of built-in functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5659: error: ‘SEEK_CUR’ undeclared (first use in this function
dcraw.c: In function ‘gamma_lut’:
dcraw.c:7496: warning: incompatible bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5665: error: ‘data_offset’ undeclared (first use in this function)
implicit declaration of built-in function ‘pow’
dcraw.c: In function ‘tifbash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5669: error: ‘thumb_offset’ undeclared (first use in this functi
f_head’:
dcraw.c:7543: warning: incompatible implicit declaration of built-bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5671: error: ‘write_thumb’ undeclared (first use in this function)
in function ‘memset’
dcraw.c:7588: warning: incompatible implicit declaratibash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5671: error: ‘jpeg_thumb’ undeclared (first use in thi
on of built-in function ‘strncpy’
dcraw.c:7591: warning: incompbash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5677: error: ‘foveon_thumb’ undeclared (first use in this function)
atible implicit declaration of built-in function ‘strcpy’
dcraw.c:7592: errobash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:5681: error: ‘meta_offset’ und
r: ‘timestamp’ undeclared (first use in
bash: dcraw.c:5681:: command not found
joxer@joxer:~$ dcraw.c:5699: warning: incompatible implicit declaration of built-in f
dcraw.c:7592: warning: assignment makes pointer from integer without a
bash: dcraw.c:5699:: command not found
joxer@joxer:~$ dcraw.c:5705: error: ‘timestamp’ undeclared (first use in this function
bash: syntax error near unexpected token `('
dcraw.c:7593: warning: incompatible implicit declaration of built-in functi
joxer@joxer:~$ dcraw.c: In function ‘adobe_coeff’:
dcraw.c:7594: error: dereferencing poin
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:6070: warning: incompatible implicit declaration of built-in function ‘sprintf’
dcraw.c:7594: error: dereferencing pointer to incomplete type
dcraw.c:7594: error: dereferebash: dcraw.c:6070:: command not found
joxer@joxer:~$ dcraw.c:6072: warning: incompatible implicit declaration of built-in function ‘strlen’
ncing pointer to incomplete type
dcraw.c:7594: error: dereferencing pointer to incomplete tbash: dcraw.c:6072:: command not found
joxer@joxer:~$ dcraw.c: In function ‘guess_byte_order’:
ype
dcraw.c:7594: error: dereferencing pointebash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:6108: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
r to incomplete type
dcraw.c:7594: error: dereferencing pointer to incojoxer@joxer:~$ dcraw.c: In function ‘identify’:
mplete type
dcraw.c: At top level:
dcbash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:6198: warning: incompatible implicit declaration of built-in function ‘memset’
raw.c:7598: error: expected ‘)’ before ‘*’ token
dcraw.c:7620: error: expected ‘)bash: dcraw.c:6198:: command not found
joxer@joxer:~$ dcraw.c:6199: error: ‘thumb_offset’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
’ before ‘*’ token
dcraw.c: In function ‘main’:
dcraw.c:7669: error: sjoxer@joxer:~$ dcraw.c:6201: error: ‘write_thumb’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
torage size of ‘ut’ isn’t known
dcraw.c:7670: error: ‘FILE’ undeclarejoxer@joxer:~$ dcraw.c:6201: error: ‘jpeg_thumb’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
d (first use in this function)
dcraw.c:7670: error: ‘ofp’ undeclared (firsjoxer@joxer:~$ dcraw.c:6202: error: ‘data_offset’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
t use in this function)
dcraw.c:7670: error: ‘stdout’ undeclared (first usejoxer@joxer:~$ dcraw.c:6204: error: ‘timestamp’ undeclared (first use 
bash: syntax error near unexpected token `('
 in this function)
dcraw.c:7686: warning: incompatible implijoxer@joxer:~$ dcraw.c:6220: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
cit declaration of built-in function ‘printf’
dcraw.c:7727: warningjoxer@joxer:~$ dcraw.c:6220: error: ‘SEEK_SET’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
: incompatible implicit declaration of built-in function ‘strchr’
dcraw.joxer@joxer:~$ dcraw.c:6222: error: ‘SEEK_END’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
c:7730: warning: incompatible implicit declaration of built-in function ‘f
joxer@joxer:~$ dcraw.c:6224: warning: passing argument 2 of ‘my_memmem’ makes pointer from integer wi
dcraw.c:7730: error: ‘stderr’ undeclared (first use in this function)
dcraw.c:7777: wabash: dcraw.c:6224:: command not found
joxer@joxer:~$ dcraw.c:6224: error: too many argument
rning: incompatible implicit declaratio
bash: dcraw.c:6224:: command not found
joxer@joxer:~$ dcraw.c:6225: warning: passing argument 2 of ‘my_memmem’ makes poi
dcraw.c:7784: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:6225:: command not found
joxer@joxer:~$ dcraw.c:6225: error: too many arguments to function ‘my_memmem’
dcraw.c:7789: warning: incompatible implicit declaration of built-i
bash: dcraw.c:6225:: command not found
joxer@joxer:~$ dcraw.c:6244: warning: incompatible implicit d
dcraw.c:7804: error: ‘failure’ undeclared 
bash: dcraw.c:6244:: command not found
joxer@joxer:~$ dcraw.c:6251: warning: incompatible implicit declaration of built-in f
dcraw.c:7805: error: ‘ifp’ undeclared (first use in this function)
bash: dcraw.c:6251:: command not found
joxer@joxer:~$ dcraw.c:6254: warning: incompatible implicit declaration of built-in 
dcraw.c:7824: error: ‘timestamp’ undeclared (first use in this fu
bash: dcraw.c:6254:: command not found
joxer@joxer:~$ dcraw.c:6257: warning: incompatible im
dcraw.c:7825: warning: incompatible im
bash: dcraw.c:6257:: command not found
joxer@joxer:~$ dcraw.c:6290: warning: incompatible implicit declaration o
dcraw.c:7827: warning: incompatible implicit declaration o
bash: dcraw.c:6290:: command not found
joxer@joxer:~$ dcraw.c:6299: warning: incompatible implicit declaration of built-in f
dcraw.c:7836: error: ‘write_fun’ undeclared (first use in this fun
bash: dcraw.c:6299:: command not found
joxer@joxer:~$ dcraw.c:6300: warning: incompatible implicit declaration of built-in function ‘str
dcraw.c:7836: error: ‘write_ppm_tiff’ undeclared (first use in this function)
dcbash: dcraw.c:6300:: command not found
joxer@joxer:~$ dcraw.c:6303: warning: incompatible implicit declaration of built-in function ‘strlen
raw.c:7838: error: ‘thumb_offset’ undeclared (first use in this function)
dcraw.c:78bash: dcraw.c:6303:: command not found
joxer@joxer:~$ dcraw.c:6309: warning: incompatible implicit declaration of built-in f
39: warning: incompatible implicit declaration of built-in function ‘
bash: dcraw.c:6309:: command not found
joxer@joxer:~$ dcraw.c:6675: warning: incompatible implicit declaration of built-in functi
dcraw.c:7843: error: ‘data_offset’ undeclared (first use in this functi
bash: dcraw.c:6675:: command not found
joxer@joxer:~$ dcraw.c:7072: error: ‘layer_thumb
dcraw.c:7848: error: ‘SEEK_SET’ u
bash: dcraw.c:7072:: command not found
joxer@joxer:~$ &#65533;&#65533;dcraw.c:7198: warning: incompatible implicit declaration of built-in f
dcraw.c:7849: error: ‘write_thumb’ undeclared (first use in this f
bash: &#65533;&#65533;dcraw.c:7198:: command not found
joxer@joxer:~$ dcraw.c:7212: warning: incompatible im
dcraw.c:7858: warning: incompatible im
bash: dcraw.c:7212:: command not found
joxer@joxer:~$ dcraw.c:7212: error: ‘stderr’ undeclared (first use in this functi
dcraw.c:7883: warning: incompatible implicit declaration of built-in f
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c: In function ‘convert_to_rgb’:
dcraw.c:7894: warning: incompatible implic
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7328: warning: incompatible implicit declaration of built-in function ‘memcpy’
dcraw.c:7903: warning: incompatible implicit declaration of built-in function ‘printf’
bash: dcraw.c:7328:: command not found
joxer@joxer:~$ dcraw.c:7332: warning: incompatible implicit declaration of built-in function ‘calloc’
dcraw.c:7920: warning: incompatible implicit declaration of built-in function ‘printf’
bash: dcraw.c:7332:: command not found
joxer@joxer:~$ dcraw.c:7343: warning: incompatible implicit declaration
dcraw.c:7926: warning: incompatible implicit declaration
bash: dcraw.c:7343:: command not found
joxer@joxer:~$ dcraw.c:7362: warning: incompatible implicit declaration of built-in f
dcraw.c:7929: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:7362:: command not found
joxer@joxer:~$ dcraw.c:7370: warning: incompatible implicit declaration of built-in functi
dcraw.c:7932: warning: incompatible implicit declaration of built-in functi
bash: dcraw.c:7370:: command not found
joxer@joxer:~$ dcraw.c:7370: error: ‘stderr’ undeclared (first use in this function)
dcraw.c:7976: error: ‘jpeg_thumb’ undeclared (first use in this funct
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7373: warning: incompatible implicit declaration of built-in function 
dcraw.c:7982: warning: incompatible implicit declaration of built-in function 
bash: dcraw.c:7373:: command not found
joxer@joxer:~$ dcraw.c: In function ‘fuji_rotate’:
dcraw.c:7982: warning: incompatible imp
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7403: warning: incompatible implicit declaration of built-in function ‘fpri
dcraw.c:7985: warning: incompatible implicit declaration of built-in function ‘strc
bash: dcraw.c:7403:: command not found
joxer@joxer:~$ dcraw.c:7403: error: ‘stderr’ undeclared (first use in
dcraw.c:7988: warning: incompatible implicit declaration o
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7405: warning: incompatible imp
dcraw.c:7990: warning: incompatible imp
bash: dcraw.c:7405:: command not found
joxer@joxer:~$ dcraw.c:7408: warning: incompatible implicit declaration of built-in f
dcraw.c:7991: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:7408:: command not found
joxer@joxer:~$ dcraw.c: In function ‘stretch’:
dcraw.c:7993: warning: incompatible
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7438: warning: incompatible implicit declaration of built-in function 
joxer@joxer:~/Desktop$ bash: dcraw.c:7438:: command not found
joxer@joxer:~$ &#65533;&#65533;dcraw.c:7438: error: ‘stderr’ undeclared (first use in this functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7441: warning: incompatible implicit declaration of built-in functi
bash: dcraw.c:7441:: command not found
joxer@joxer:~$ dcraw.c:7453: warning: incompatible implicit declaration of built-in functi
bash: dcraw.c:7453:: command not found
joxer@joxer:~$ dcraw.c: In function ‘gamma_lut’:
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7496: warning: incompatible implicit declaration of built-in function ‘pow’
bash: dcraw.c:7496:: command not found
joxer@joxer:~$ dcraw.c: In function ‘tiff_head’:
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7543: warning: incompatible implicit declaration of built-in function ‘memset’
bash: dcraw.c:7543:: command not found
joxer@joxer:~$ dcraw.c:7588: warning: incompatible implicit declaration of built-in function ‘strncpy’
bash: dcraw.c:7588:: command not found
joxer@joxer:~$ dcraw.c:7591: warning: incompatible implicit declaration of built-in function ‘strcpy’
bash: dcraw.c:7591:: command not found
joxer@joxer:~$ dcraw.c:7592: error: ‘timestamp’ undeclared (first use in
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7592: warning: assignment makes pointer from integer without a
bash: dcraw.c:7592:: command not found
joxer@joxer:~$ dcraw.c:7593: warning: incompatible implicit declaration of built-in functi
bash: dcraw.c:7593:: command not found
joxer@joxer:~$ dcraw.c:7594: error: dereferencing poin
bash: dcraw.c:7594:: command not found
joxer@joxer:~$ dcraw.c:7594: error: dereferencing pointer to incomplete type
bash: dcraw.c:7594:: command not found
joxer@joxer:~$ dcraw.c:7594: error: dereferencing pointer to incomplete type
bash: dcraw.c:7594:: command not found
joxer@joxer:~$ dcraw.c:7594: error: dereferencing pointer to incomplete type
bash: dcraw.c:7594:: command not found
joxer@joxer:~$ dcraw.c:7594: error: dereferencing pointer to incomplete type
bash: dcraw.c:7594:: command not found
joxer@joxer:~$ dcraw.c:7594: error: dereferencing pointer to incomplete type
bash: dcraw.c:7594:: command not found
joxer@joxer:~$ dcraw.c: At top level:
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7598: error: expected ‘)’ before ‘*’ token
bash: syntax error near unexpected token `)'
joxer@joxer:~$ dcraw.c:7620: error: expected ‘)’ before ‘*’ token
bash: syntax error near unexpected token `)'
joxer@joxer:~$ dcraw.c: In function ‘main’:
bash: dcraw.c:: command not found
joxer@joxer:~$ dcraw.c:7669: error: storage size of ‘ut’ isn’t known
bash: dcraw.c:7669:: command not found
joxer@joxer:~$ dcraw.c:7670: error: ‘FILE’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7670: error: ‘ofp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7670: error: ‘stdout’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7686: warning: incompatible implicit declaration of built-in function ‘printf’
bash: dcraw.c:7686:: command not found
joxer@joxer:~$ dcraw.c:7727: warning: incompatible implicit declaration of built-in function ‘strchr’
bash: dcraw.c:7727:: command not found
joxer@joxer:~$ dcraw.c:7730: warning: incompatible implicit declaration of built-in function ‘f
bash: dcraw.c:7730:: command not found
joxer@joxer:~$ dcraw.c:7730: error: ‘stderr’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7777: warning: incompatible implicit declaratio
bash: dcraw.c:7777:: command not found
joxer@joxer:~$ dcraw.c:7784: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:7784:: command not found
joxer@joxer:~$ dcraw.c:7789: warning: incompatible implicit declaration of built-i
bash: dcraw.c:7789:: command not found
joxer@joxer:~$ dcraw.c:7804: error: ‘failure’ undeclared 
bash: dcraw.c:7804:: command not found
joxer@joxer:~$ dcraw.c:7805: error: ‘ifp’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7824: error: ‘timestamp’ undeclared (first use in this fu
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7825: warning: incompatible im
bash: dcraw.c:7825:: command not found
joxer@joxer:~$ dcraw.c:7827: warning: incompatible implicit declaration o
bash: dcraw.c:7827:: command not found
joxer@joxer:~$ dcraw.c:7836: error: ‘write_fun’ undeclared (first use in this fun
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7836: error: ‘write_ppm_tiff’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7838: error: ‘thumb_offset’ undeclared (first use in this function)
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7839: warning: incompatible implicit declaration of built-in function ‘
bash: dcraw.c:7839:: command not found
joxer@joxer:~$ dcraw.c:7843: error: ‘data_offset’ undeclared (first use in this functi
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7848: error: ‘SEEK_SET’ u
bash: dcraw.c:7848:: command not found
joxer@joxer:~$ dcraw.c:7849: error: ‘write_thumb’ undeclared (first use in this f
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7858: warning: incompatible im
bash: dcraw.c:7858:: command not found
joxer@joxer:~$ dcraw.c:7883: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:7883:: command not found
joxer@joxer:~$ dcraw.c:7894: warning: incompatible implic
bash: dcraw.c:7894:: command not found
joxer@joxer:~$ dcraw.c:7903: warning: incompatible implicit declaration of built-in function ‘printf’
bash: dcraw.c:7903:: command not found
joxer@joxer:~$ dcraw.c:7920: warning: incompatible implicit declaration of built-in function ‘printf’
bash: dcraw.c:7920:: command not found
joxer@joxer:~$ dcraw.c:7926: warning: incompatible implicit declaration
bash: dcraw.c:7926:: command not found
joxer@joxer:~$ dcraw.c:7929: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:7929:: command not found
joxer@joxer:~$ dcraw.c:7932: warning: incompatible implicit declaration of built-in functi
bash: dcraw.c:7932:: command not found
joxer@joxer:~$ dcraw.c:7976: error: ‘jpeg_thumb’ undeclared (first use in this funct
bash: syntax error near unexpected token `('
joxer@joxer:~$ dcraw.c:7982: warning: incompatible implicit declaration of built-in function 
bash: dcraw.c:7982:: command not found
joxer@joxer:~$ dcraw.c:7982: warning: incompatible imp
bash: dcraw.c:7982:: command not found
joxer@joxer:~$ dcraw.c:7985: warning: incompatible implicit declaration of built-in function ‘strc
bash: dcraw.c:7985:: command not found
joxer@joxer:~$ dcraw.c:7988: warning: incompatible implicit declaration o
bash: dcraw.c:7988:: command not found
joxer@joxer:~$ dcraw.c:7990: warning: incompatible imp
bash: dcraw.c:7990:: command not found
joxer@joxer:~$ dcraw.c:7991: warning: incompatible implicit declaration of built-in f
bash: dcraw.c:7991:: command not found
joxer@joxer:~$ dcraw.c:7993: warning: incompatible
bash: dcraw.c:7993:: command not found

```

Thanks very much in advance!

---

### Post by gobbles414 on 2007-08-21
...Forgot to mention that I'm using Ubuntu Feisty.

---

### Post by gobbles414 on 2007-08-22
bump

---

### Post by gobbles414 on 2007-08-23
Oops! I didn't have *build-essential* installed. After installing that in Synaptic, I was able to compile dcraw. Then all that I had to do was _sudo mv dcraw /usr/bin_.

---

