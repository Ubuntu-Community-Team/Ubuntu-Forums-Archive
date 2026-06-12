---
title: "gnome compile error"
date: 2007-03-28
forum: General Help
---

### Post by Choad on 2007-03-28
ok im trying to compile gnome from gnome.org using garnome.

i had several errors throughout but got passed them by installing the relevent dev package, now tho i have a different error and im not sure how to fix it

```
e2k-kerberos.c:31:18: error: krb5.h: No such file or directory
e2k-kerberos.c:34: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'e2k_kerberos_context_new'
e2k-kerberos.c: In function 'krb5_result_to_e2k_kerberos_result':
e2k-kerberos.c:56: error: 'KRB5KDC_ERR_C_PRINCIPAL_UNKNOWN' undeclared (first use in this function)
e2k-kerberos.c:56: error: (Each undeclared identifier is reported only once
e2k-kerberos.c:56: error: for each function it appears in.)
e2k-kerberos.c:59: error: 'KRB5KRB_AP_ERR_BAD_INTEGRITY' undeclared (first use in this function)
e2k-kerberos.c:60: error: 'KRB5KDC_ERR_PREAUTH_FAILED' undeclared (first use in this function)
e2k-kerberos.c:63: error: 'KRB5KDC_ERR_KEY_EXP' undeclared (first use in this function)
e2k-kerberos.c:66: error: 'KRB5_KDC_UNREACH' undeclared (first use in this function)
e2k-kerberos.c:69: error: 'KRB5KRB_AP_ERR_SKEW' undeclared (first use in this function)
e2k-kerberos.c: At top level:
e2k-kerberos.c:79: error: expected ')' before 'ctx'
e2k-kerberos.c: In function 'e2k_kerberos_change_password':
e2k-kerberos.c:119: error: 'krb5_context' undeclared (first use in this function)
e2k-kerberos.c:119: error: expected ';' before 'ctx'
e2k-kerberos.c:120: error: 'krb5_creds' undeclared (first use in this function)
e2k-kerberos.c:120: error: expected ';' before 'creds'
e2k-kerberos.c:121: error: 'krb5_data' undeclared (first use in this function)
e2k-kerberos.c:121: error: expected ';' before 'res_code_string'
e2k-kerberos.c:125: error: 'ctx' undeclared (first use in this function)
e2k-kerberos.c:125: warning: implicit declaration of function 'e2k_kerberos_context_new'
e2k-kerberos.c:129: warning: implicit declaration of function 'get_init_cred'
e2k-kerberos.c:130: error: 'creds' undeclared (first use in this function)
e2k-kerberos.c:132: warning: implicit declaration of function 'krb5_free_context'
e2k-kerberos.c:136: warning: implicit declaration of function 'krb5_change_password'
e2k-kerberos.c:137: error: 'res_code_string' undeclared (first use in this function)
e2k-kerberos.c:137: error: 'res_string' undeclared (first use in this function)
e2k-kerberos.c:138: warning: implicit declaration of function 'krb5_free_cred_contents'
e2k-kerberos.c:139: warning: implicit declaration of function 'krb5_free_data_contents'
e2k-kerberos.c: In function 'e2k_kerberos_check_password':
e2k-kerberos.c:167: error: 'krb5_context' undeclared (first use in this function)
e2k-kerberos.c:167: error: expected ';' before 'ctx'
e2k-kerberos.c:168: error: 'krb5_creds' undeclared (first use in this function)
e2k-kerberos.c:168: error: expected ';' before 'creds'
e2k-kerberos.c:171: error: 'ctx' undeclared (first use in this function)
e2k-kerberos.c:175: error: 'creds' undeclared (first use in this function)
make[11]: *** [e2k-kerberos.lo] Error 1
make[11]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server/work/main.d/evolution-data-server-1.10.0/servers/exchange/lib'
make[10]: *** [all] Error 2
make[10]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server/work/main.d/evolution-data-server-1.10.0/servers/exchange/lib'
make[9]: *** [all-recursive] Error 1
make[9]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server/work/main.d/evolution-data-server-1.10.0/servers/exchange'
make[8]: *** [all-recursive] Error 1
make[8]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server/work/main.d/evolution-data-server-1.10.0/servers'
make[7]: *** [all-recursive] Error 1
make[7]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server/work/main.d/evolution-data-server-1.10.0'
make[6]: *** [all] Error 2
make[6]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server/work/main.d/evolution-data-server-1.10.0'
make[5]: *** [build-work/main.d/evolution-data-server-1.10.0/Makefile] Error 2
make[5]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/evolution-data-server'
make[4]: *** [../../desktop/evolution-data-server/cookies/main.d/install] Error 2
make[4]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/desktop/gnome-panel'
make[3]: *** [../../desktop/gnome-panel/cookies/main.d/install] Error 2
make[3]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/bindings/gnome-python'
make[2]: *** [../../bindings/gnome-python/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/admin/pessulus'
make[1]: *** [paranoid-install] Error 2
make[1]: Leaving directory `/home/richard/Desktop/garnome-2.18.0/admin'
make: *** [paranoid-install] Error 2
richard@richard-laptop:~/Desktop/garnome-2.18.0$ 

```

---

### Post by wonk-o-matic on 2007-03-28
Did you install the build-essentials package?

---

### Post by Choad on 2007-03-28
heh, yes

---

### Post by silas_irl on 2007-03-28
It sounds like you might have to alter the make file(s) that came with the source.  The very first line, it can't find a header file, so you might need to alter the include search path to g++/gcc.

---

