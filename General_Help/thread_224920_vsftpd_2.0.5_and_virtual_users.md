---
title: "vsftpd 2.0.5 and virtual users"
date: 2006-07-28
forum: General Help
---

### Post by nix4me on 2006-07-28
Has anyone been able to install the new vsftpd 2.0.5 from source with ssl?

I get errors on the make.

Also, has anyone been able to get virtual users to work with vsftpd?

nix4me

---

### Post by taurus on 2006-07-28
What kind of error do you get from running the make command?  Wanna share!!!

---

### Post by nix4me on 2006-07-28
```
gcc -c ssl.c -g -O2 -Wall -W -Wshadow  -idirafter dummyinc
ssl.c:27:25: error: openssl/err.h: No such file or directory
ssl.c:28:26: error: openssl/rand.h: No such file or directory
ssl.c:29:25: error: openssl/bio.h: No such file or directory
ssl.c:32: error: syntax error before ‘*’ token
ssl.c:32: warning: type defaults to ‘int’ in declaration of ‘get_ssl’
ssl.c:32: warning: data definition has no type or storage class
ssl.c:36: error: syntax error before ‘*’ token
ssl.c: In function ‘ssl_init’:
ssl.c:45: error: ‘SSL_CTX’ undeclared (first use in this function)
ssl.c:45: error: (Each undeclared identifier is reported only once
ssl.c:45: error: for each function it appears in.)
ssl.c:45: error: ‘p_ctx’ undeclared (first use in this function)
ssl.c:47: warning: implicit declaration of function ‘SSL_library_init’
ssl.c:48: warning: implicit declaration of function ‘SSL_CTX_new’
ssl.c:48: warning: implicit declaration of function ‘SSLv23_server_method’
ssl.c:49: error: ‘NULL’ undeclared (first use in this function)
ssl.c:53: error: ‘SSL_OP_ALL’ undeclared (first use in this function)
ssl.c:56: error: ‘SSL_OP_NO_SSLv2’ undeclared (first use in this function)
ssl.c:60: error: ‘SSL_OP_NO_SSLv3’ undeclared (first use in this function)
ssl.c:64: error: ‘SSL_OP_NO_TLSv1’ undeclared (first use in this function)
ssl.c:66: warning: implicit declaration of function ‘SSL_CTX_set_options’
ssl.c:74: warning: implicit declaration of function ‘SSL_CTX_use_certificate_chain_file’
ssl.c:78: warning: implicit declaration of function ‘SSL_CTX_use_PrivateKey_file’
ssl.c:78: error: ‘X509_FILETYPE_PEM’ undeclared (first use in this function)
ssl.c:100: warning: implicit declaration of function ‘SSL_CTX_set_cipher_list’
ssl.c:104: warning: implicit declaration of function ‘RAND_status’
ssl.c: In function ‘ssl_getline’:
ssl.c:195: warning: implicit declaration of function ‘SSL_read’
ssl.c: In function ‘ssl_read’:
ssl.c:218: error: ‘SSL’ undeclared (first use in this function)
ssl.c:218: error: syntax error before ‘)’ token
ssl.c:219: warning: implicit declaration of function ‘SSL_get_error’
ssl.c:219: error: syntax error before ‘)’ token
ssl.c:221: error: ‘SSL_ERROR_WANT_READ’ undeclared (first use in this function)
ssl.c:222: error: ‘SSL_ERROR_WANT_WRITE’ undeclared (first use in this function)
ssl.c:212: warning: unused parameter ‘p_ssl’
ssl.c:212: warning: unused parameter ‘p_buf’
ssl.c:212: warning: unused parameter ‘len’
ssl.c: In function ‘ssl_write’:
ssl.c:233: warning: implicit declaration of function ‘SSL_write’
ssl.c:233: error: ‘SSL’ undeclared (first use in this function)
ssl.c:233: error: syntax error before ‘)’ token
ssl.c:234: error: syntax error before ‘)’ token
ssl.c:236: error: ‘SSL_ERROR_WANT_READ’ undeclared (first use in this function)
ssl.c:237: error: ‘SSL_ERROR_WANT_WRITE’ undeclared (first use in this function)
ssl.c:227: warning: unused parameter ‘p_ssl’
ssl.c:227: warning: unused parameter ‘p_buf’
ssl.c:227: warning: unused parameter ‘len’
ssl.c: In function ‘ssl_write_str’:
ssl.c:245: error: ‘SSL’ undeclared (first use in this function)
ssl.c:245: error: syntax error before ‘)’ token
ssl.c:242: warning: unused parameter ‘p_ssl’
ssl.c: In function ‘ssl_accept’:
ssl.c:256: error: ‘SSL’ undeclared (first use in this function)
ssl.c:256: error: ‘p_ssl’ undeclared (first use in this function)
ssl.c:257: error: ‘NULL’ undeclared (first use in this function)
ssl.c: In function ‘ssl_data_close’:
ssl.c:269: warning: implicit declaration of function ‘SSL_free’
ssl.c: At top level:
ssl.c:281: error: syntax error before ‘*’ token
ssl.c:283: warning: return type defaults to ‘int’
ssl.c: In function ‘get_ssl’:
ssl.c:284: error: ‘SSL’ undeclared (first use in this function)
ssl.c:284: error: ‘p_ssl’ undeclared (first use in this function)
ssl.c:284: warning: implicit declaration of function ‘SSL_new’
ssl.c:285: error: ‘NULL’ undeclared (first use in this function)
ssl.c:289: warning: implicit declaration of function ‘SSL_set_fd’
ssl.c:294: warning: implicit declaration of function ‘SSL_accept’
ssl.c: In function ‘ssl_session_init’:
ssl.c:306: error: ‘SSL’ undeclared (first use in this function)
ssl.c:306: error: ‘p_ssl’ undeclared (first use in this function)
ssl.c:307: error: ‘NULL’ undeclared (first use in this function)
ssl.c: In function ‘get_ssl_error’:
ssl.c:319: warning: implicit declaration of function ‘SSL_load_error_strings’
ssl.c:320: warning: implicit declaration of function ‘ERR_error_string’
ssl.c:320: warning: implicit declaration of function ‘ERR_get_error’
ssl.c:320: error: ‘NULL’ undeclared (first use in this function)
ssl.c:320: warning: return makes pointer from integer without a cast
ssl.c: At top level:
ssl.c:323: error: syntax error before ‘*’ token
ssl.c: In function ‘setup_bio_callbacks’:
ssl.c:325: error: ‘BIO’ undeclared (first use in this function)
ssl.c:325: error: ‘p_bio’ undeclared (first use in this function)
ssl.c:325: warning: implicit declaration of function ‘SSL_get_rbio’
ssl.c:325: error: ‘p_ssl’ undeclared (first use in this function)
ssl.c:326: warning: implicit declaration of function ‘BIO_set_callback’
ssl.c:327: warning: implicit declaration of function ‘SSL_get_wbio’
ssl.c: At top level:
ssl.c:333: error: syntax error before ‘*’ token
ssl.c: In function ‘bio_callback’:
ssl.c:337: error: ‘p_arg’ undeclared (first use in this function)
ssl.c:338: error: ‘argi’ undeclared (first use in this function)
ssl.c:339: error: ‘argl’ undeclared (first use in this function)
ssl.c:340: error: ‘oper’ undeclared (first use in this function)
ssl.c:340: error: ‘BIO_CB_READ’ undeclared (first use in this function)
ssl.c:340: error: ‘BIO_CB_RETURN’ undeclared (first use in this function)
ssl.c:341: error: ‘BIO_CB_WRITE’ undeclared (first use in this function)
ssl.c:343: error: ‘ret’ undeclared (first use in this function)
ssl.c:344: warning: implicit declaration of function ‘BIO_get_fd’
ssl.c:344: error: ‘p_bio’ undeclared (first use in this function)
ssl.c:344: error: ‘NULL’ undeclared (first use in this function)
make: *** [ssl.o] Error 1

```

nix4me

---

