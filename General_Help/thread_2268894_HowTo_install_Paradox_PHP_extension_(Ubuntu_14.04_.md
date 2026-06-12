---
title: "HowTo install Paradox PHP extension (Ubuntu 14.04 + PHP 5.5)"
date: 2015-03-12
forum: General Help
---

### Post by Dimas on 2015-03-12
I'm trying to install the Paradox PHP extension to a Ubuntu Server 14.04.

The easy solution may be:

```
pecl install paradox
```

But it fails with this error:

> Cannot find config.m4. Make sure that you run '/usr/bin/phpize' in the top level source directory of the module

So I tried to generate the paradox.so manually:

```
 tar -xzvf paradox-1.4.3.tgz
 phpize
 ./configure
 make
```

Ending with error: "make: *** [paradox.lo] Error 1". The complete output: [https://dl.dropboxusercontent.com/u/171128/make_output.txt](https://dl.dropboxusercontent.com/u/171128/make_output.txt)

Any idea? :-(

---

### Post by Dimas on 2015-03-12
I trying to do the same with odbtp and it ends with the same "make: *** [php_odbtp.lo] Error 1" error :- ((((

---

### Post by Nikola_Kotarov on 2015-04-22
I had the same problem so I made a patch for it. You need to apply it before trying to compile it.

```

--- paradox-1.4.3/paradox.c    2007-09-25 15:12:42.000000000 +0300
+++ paradox.c    2015-04-22 16:42:13.399878251 +0300
@@ -48,7 +48,7 @@
  *
  * Every user visible function must have an entry in paradox_functions[].
  */
-function_entry paradox_functions[] = {
+zend_function_entry paradox_functions[] = {
     PHP_FE(px_new, NULL)
     PHP_FE(px_open_fp, NULL)
     PHP_FE(px_create_fp, NULL)
@@ -89,7 +89,7 @@
 };
 /* }}} */

-function_entry paradox_funcs_db[] = {
+zend_function_entry paradox_funcs_db[] = {
     PHP_ME_MAPPING(__construct, px_new, NULL, 0)
     PHP_ME_MAPPING(open_fp, px_open_fp, NULL, 0)
     PHP_ME_MAPPING(create_fp, px_create_fp, NULL, 0)
@@ -283,7 +283,7 @@

     ALLOC_HASHTABLE(intern->zo.properties);
     zend_hash_init(intern->zo.properties, 0, NULL, ZVAL_PTR_DTOR, 0);
-    zend_hash_copy(intern->zo.properties, &class_type->default_properties, (copy_ctor_func_t) zval_add_ref, (void *) &tmp, sizeof(zval *));
+    object_properties_init((zend_object*) &(intern->zo), class_type);

     intern->ptr = PX_new2(px_custom_errorhandler, px_emalloc, px_erealloc, px_efree);
     retval->handle = zend_objects_store_put(intern, paradox_object_dtor, NULL, NULL TSRMLS_CC);

```

---

