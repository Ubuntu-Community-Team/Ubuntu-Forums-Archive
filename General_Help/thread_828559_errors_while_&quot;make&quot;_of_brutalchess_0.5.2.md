---
title: "errors while &quot;make&quot; of brutalchess 0.5.2"
date: 2008-06-13
forum: General Help
---

### Post by deci on 2008-06-13
hey everybody, 
I was just busy installing brutalchess while I encountered this problem ...
while I hit the command make it gave me a lot of errors
./configure worked out just fine ending without errors so thats ok
So I did make > log
Could any of you guys tell me what I need to do to fix the problem(s) and finish the make command without errors ?
here is the log ...


cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
Making all in src
make[1]: Entering directory `/home/yannick/brutalchess-0.5.2/src'
cd .. && make  am--refresh
make[2]: Entering directory `/home/yannick/brutalchess-0.5.2'
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
make[2]: Leaving directory `/home/yannick/brutalchess-0.5.2'
make[2]: Entering directory `/home/yannick/brutalchess-0.5.2'
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
make[2]: Leaving directory `/home/yannick/brutalchess-0.5.2'
cd .. && make  am--refresh
make[2]: Entering directory `/home/yannick/brutalchess-0.5.2'
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
make[2]: Leaving directory `/home/yannick/brutalchess-0.5.2'
make  all-am
make[2]: Entering directory `/home/yannick/brutalchess-0.5.2/src'
cd .. && make  am--refresh
make[3]: Entering directory `/home/yannick/brutalchess-0.5.2'
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
make[3]: Leaving directory `/home/yannick/brutalchess-0.5.2'
make[3]: Entering directory `/home/yannick/brutalchess-0.5.2'
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
make[3]: Leaving directory `/home/yannick/brutalchess-0.5.2'
cd .. && make  am--refresh
make[3]: Entering directory `/home/yannick/brutalchess-0.5.2'
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run aclocal-1.8 
 cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run automake-1.8 --foreign 
cd . && /bin/bash /home/yannick/brutalchess-0.5.2/missing --run autoconf
make[3]: Leaving directory `/home/yannick/brutalchess-0.5.2'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -DPREFIX_DIR=\"/usr/local/share/brutalchess/\" -DMODELS_DIR=\"/usr/local/share/brutalchess/models/\" -DART_DIR=\"/usr/local/share/brutalchess/art/\" -DFONTS_DIR=\"/usr/local/share/brutalchess/fonts/\"    -g -O2  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/local/include/freetype2 -I/usr/local/include -MT basicset.o -MD -MP -MF ".deps/basicset.Tpo" -c -o basicset.o basicset.cpp; \
	then mv -f ".deps/basicset.Tpo" ".deps/basicset.Po"; else rm -f ".deps/basicset.Tpo"; exit 1; fi
make[2]: Leaving directory `/home/yannick/brutalchess-0.5.2/src'
make[1]: Leaving directory `/home/yannick/brutalchess-0.5.2/src'

---

### Post by PmDematagoda on 2008-06-13
Hasn't it finished successfully? From the log it looks like there are no errors.

Also this thread is moved to the General Help section.

---

### Post by deci on 2008-06-13
seems like I gave you the wrong information
here is a little snipet of what happens in console after typing make and hitting return


/usr/local/include/SDL/SDL_opengl.h:6279: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6279: error: &#8216;GLfloat&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6279: error: &#8216;GLfloat&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6279: error: &#8216;GLfloat&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6279: error: &#8216;GLfloat&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6280: error: typedef &#8216;PFNGLPROGRAMNAMEDPARAMETER4DNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6280: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6280: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6280: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6280: error: &#8216;GLdouble&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6280: error: &#8216;GLdouble&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6280: error: &#8216;GLdouble&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6280: error: &#8216;GLdouble&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6281: error: typedef &#8216;PFNGLPROGRAMNAMEDPARAMETER4FVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6281: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6281: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6281: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6281: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6282: error: typedef &#8216;PFNGLPROGRAMNAMEDPARAMETER4DVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6282: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6282: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6282: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6282: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6283: error: typedef &#8216;PFNGLGETPROGRAMNAMEDPARAMETERFVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6283: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6283: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6283: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6283: error: &#8216;GLfloat&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6283: error: &#8216;params&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6284: error: typedef &#8216;PFNGLGETPROGRAMNAMEDPARAMETERDVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6284: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6284: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6284: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6284: error: &#8216;GLdouble&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6284: error: &#8216;params&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6357: error: typedef &#8216;PFNGLMULTITEXCOORD1HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6357: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6357: error: expected primary-expression before &#8216;s&#8217;
/usr/local/include/SDL/SDL_opengl.h:6358: error: typedef &#8216;PFNGLMULTITEXCOORD1HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6358: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6358: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6359: error: typedef &#8216;PFNGLMULTITEXCOORD2HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6359: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6359: error: expected primary-expression before &#8216;s&#8217;
/usr/local/include/SDL/SDL_opengl.h:6359: error: expected primary-expression before &#8216;t&#8217;
/usr/local/include/SDL/SDL_opengl.h:6360: error: typedef &#8216;PFNGLMULTITEXCOORD2HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6360: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6360: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6361: error: typedef &#8216;PFNGLMULTITEXCOORD3HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6361: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6361: error: expected primary-expression before &#8216;s&#8217;
/usr/local/include/SDL/SDL_opengl.h:6361: error: expected primary-expression before &#8216;t&#8217;
/usr/local/include/SDL/SDL_opengl.h:6361: error: expected primary-expression before &#8216;r&#8217;
/usr/local/include/SDL/SDL_opengl.h:6362: error: typedef &#8216;PFNGLMULTITEXCOORD3HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6362: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6362: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6363: error: typedef &#8216;PFNGLMULTITEXCOORD4HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6363: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6363: error: expected primary-expression before &#8216;s&#8217;
/usr/local/include/SDL/SDL_opengl.h:6363: error: expected primary-expression before &#8216;t&#8217;
/usr/local/include/SDL/SDL_opengl.h:6363: error: expected primary-expression before &#8216;r&#8217;
/usr/local/include/SDL/SDL_opengl.h:6363: error: expected primary-expression before &#8216;q&#8217;
/usr/local/include/SDL/SDL_opengl.h:6364: error: typedef &#8216;PFNGLMULTITEXCOORD4HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6364: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6364: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6371: error: typedef &#8216;PFNGLVERTEXATTRIB1HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6371: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6371: error: expected primary-expression before &#8216;x&#8217;
/usr/local/include/SDL/SDL_opengl.h:6372: error: typedef &#8216;PFNGLVERTEXATTRIB1HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6372: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6372: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6373: error: typedef &#8216;PFNGLVERTEXATTRIB2HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6373: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6373: error: expected primary-expression before &#8216;x&#8217;
/usr/local/include/SDL/SDL_opengl.h:6373: error: expected primary-expression before &#8216;y&#8217;
/usr/local/include/SDL/SDL_opengl.h:6374: error: typedef &#8216;PFNGLVERTEXATTRIB2HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6374: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6374: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6375: error: typedef &#8216;PFNGLVERTEXATTRIB3HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6375: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6375: error: expected primary-expression before &#8216;x&#8217;
/usr/local/include/SDL/SDL_opengl.h:6375: error: expected primary-expression before &#8216;y&#8217;
/usr/local/include/SDL/SDL_opengl.h:6375: error: expected primary-expression before &#8216;z&#8217;
/usr/local/include/SDL/SDL_opengl.h:6376: error: typedef &#8216;PFNGLVERTEXATTRIB3HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6376: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6376: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6377: error: typedef &#8216;PFNGLVERTEXATTRIB4HNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6377: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6377: error: expected primary-expression before &#8216;x&#8217;
/usr/local/include/SDL/SDL_opengl.h:6377: error: expected primary-expression before &#8216;y&#8217;
/usr/local/include/SDL/SDL_opengl.h:6377: error: expected primary-expression before &#8216;z&#8217;
/usr/local/include/SDL/SDL_opengl.h:6377: error: expected primary-expression before &#8216;w&#8217;
/usr/local/include/SDL/SDL_opengl.h:6378: error: typedef &#8216;PFNGLVERTEXATTRIB4HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6378: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6378: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6379: error: typedef &#8216;PFNGLVERTEXATTRIBS1HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6379: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6379: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6379: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6380: error: typedef &#8216;PFNGLVERTEXATTRIBS2HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6380: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6380: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6380: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6381: error: typedef &#8216;PFNGLVERTEXATTRIBS3HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6381: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6381: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6381: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6382: error: typedef &#8216;PFNGLVERTEXATTRIBS4HVNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6382: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6382: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6382: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6391: error: typedef &#8216;PFNGLPIXELDATARANGENVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6391: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6391: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6391: error: &#8216;GLvoid&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6391: error: &#8216;pointer&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6392: error: typedef &#8216;PFNGLFLUSHPIXELDATARANGENVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6392: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6402: error: typedef &#8216;PFNGLPRIMITIVERESTARTINDEXNVPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6402: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6419: error: expected initializer before &#8216;*&#8217; token
/usr/local/include/SDL/SDL_opengl.h:6420: error: typedef &#8216;PFNGLUNMAPOBJECTBUFFERATIPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6420: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6429: error: typedef &#8216;PFNGLSTENCILOPSEPARATEATIPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6429: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6429: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6429: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6429: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6430: error: typedef &#8216;PFNGLSTENCILFUNCSEPARATEATIPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6430: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6430: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6430: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6430: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: typedef &#8216;PFNGLVERTEXATTRIBARRAYOBJECTATIPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLboolean&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6440: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6441: error: typedef &#8216;PFNGLGETVERTEXATTRIBARRAYOBJECTFVATIPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6441: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6441: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6441: error: &#8216;GLfloat&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6441: error: &#8216;params&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6442: error: typedef &#8216;PFNGLGETVERTEXATTRIBARRAYOBJECTIVATIPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6442: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6442: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6442: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6442: error: &#8216;params&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6454: error: typedef &#8216;PFNGLDEPTHBOUNDSEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6454: error: &#8216;GLclampd&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6454: error: &#8216;GLclampd&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6466: error: typedef &#8216;PFNGLBLENDEQUATIONSEPARATEEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6466: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6466: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6518: error: ISO C++ forbids declaration of &#8216;GLboolean&#8217; with no type
/usr/local/include/SDL/SDL_opengl.h:6518: error: typedef &#8216;GLboolean&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6518: error: &#8216;PFNGLISRENDERBUFFEREXTPROC&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6519: error: typedef &#8216;PFNGLBINDRENDERBUFFEREXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6519: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6519: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6520: error: typedef &#8216;PFNGLDELETERENDERBUFFERSEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6520: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6520: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6521: error: typedef &#8216;PFNGLGENRENDERBUFFERSEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6521: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6521: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6521: error: &#8216;renderbuffers&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6522: error: typedef &#8216;PFNGLRENDERBUFFERSTORAGEEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6522: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6522: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6522: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6522: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6523: error: typedef &#8216;PFNGLGETRENDERBUFFERPARAMETERIVEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6523: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6523: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6523: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6523: error: &#8216;params&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6524: error: ISO C++ forbids declaration of &#8216;GLboolean&#8217; with no type
/usr/local/include/SDL/SDL_opengl.h:6524: error: typedef &#8216;GLboolean&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6524: error: &#8216;PFNGLISFRAMEBUFFEREXTPROC&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6525: error: typedef &#8216;PFNGLBINDFRAMEBUFFEREXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6525: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6525: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6526: error: typedef &#8216;PFNGLDELETEFRAMEBUFFERSEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6526: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6526: error: expected primary-expression before &#8216;const&#8217;
/usr/local/include/SDL/SDL_opengl.h:6527: error: typedef &#8216;PFNGLGENFRAMEBUFFERSEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6527: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6527: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6527: error: &#8216;framebuffers&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6528: error: ISO C++ forbids declaration of &#8216;GLenum&#8217; with no type
/usr/local/include/SDL/SDL_opengl.h:6528: error: typedef &#8216;GLenum&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6528: error: &#8216;PFNGLCHECKFRAMEBUFFERSTATUSEXTPROC&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6529: error: typedef &#8216;PFNGLFRAMEBUFFERTEXTURE1DEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6529: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6529: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6529: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6529: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6529: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6530: error: typedef &#8216;PFNGLFRAMEBUFFERTEXTURE2DEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6530: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6530: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6530: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6530: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6530: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6531: error: typedef &#8216;PFNGLFRAMEBUFFERTEXTURE3DEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6531: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6531: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6531: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6531: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6531: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6531: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6532: error: typedef &#8216;PFNGLFRAMEBUFFERRENDERBUFFEREXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6532: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6532: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6532: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6532: error: &#8216;GLuint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6533: error: typedef &#8216;PFNGLGETFRAMEBUFFERATTACHMENTPARAMETERIVEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6533: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6533: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6533: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6533: error: &#8216;GLint&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6533: error: &#8216;params&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6534: error: typedef &#8216;PFNGLGENERATEMIPMAPEXTPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6534: error: &#8216;GLenum&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6542: error: typedef &#8216;PFNGLSTRINGMARKERGREMEDYPROC&#8217; is initialized (use __typeof__ instead)
/usr/local/include/SDL/SDL_opengl.h:6542: error: &#8216;GLsizei&#8217; was not declared in this scope
/usr/local/include/SDL/SDL_opengl.h:6542: error: expected primary-expression before &#8216;const&#8217;
In file included from pieceset.h:14,
                 from basicset.cpp:10:
objfile.h:47: error: &#8216;GLuint&#8217; does not name a type
objfile.h: In member function &#8216;void ObjFile::Point::glVertex()&#8217;:
objfile.h:56: error: &#8216;glVertex3d&#8217; was not declared in this scope
objfile.h: In member function &#8216;void ObjFile::Point::glTexCoord()&#8217;:
objfile.h:57: error: &#8216;glTexCoord3d&#8217; was not declared in this scope
In file included from piecesets.h:10,
                 from pieceset.h:105,
                 from basicset.cpp:10:
texture.h: At global scope:
texture.h:54: error: &#8216;GLuint&#8217; does not name a type
texture.h:56: error: &#8216;GLenum&#8217; does not name a type
texture.h:65: error: &#8216;GLuint&#8217; does not name a type
basicset.cpp: In member function &#8216;virtual void BasicSet::draw(const ChessGameState&)&#8217;:
basicset.cpp:149: error: &#8216;GL_SRC_ALPHA&#8217; was not declared in this scope
basicset.cpp:149: error: &#8216;GL_ONE_MINUS_SRC_ALPHA&#8217; was not declared in this scope
basicset.cpp:149: error: &#8216;glBlendFunc&#8217; was not declared in this scope
basicset.cpp:152: error: &#8216;glPushMatrix&#8217; was not declared in this scope
basicset.cpp:153: error: &#8216;glTranslated&#8217; was not declared in this scope
basicset.cpp:238: error: &#8216;glPopMatrix&#8217; was not declared in this scope
basicset.cpp: In member function &#8216;virtual void BasicSet::drawPiece(Piece*, double, bool)&#8217;:
basicset.cpp:264: error: &#8216;GL_BLEND&#8217; was not declared in this scope
basicset.cpp:264: error: &#8216;glEnable&#8217; was not declared in this scope
basicset.cpp:269: error: &#8216;glScalef&#8217; was not declared in this scope
basicset.cpp:270: error: &#8216;glRotated&#8217; was not declared in this scope
basicset.cpp:271: error: &#8216;glColor4f&#8217; was not declared in this scope
basicset.cpp:289: error: &#8216;GL_BLEND&#8217; was not declared in this scope
basicset.cpp:289: error: &#8216;glDisable&#8217; was not declared in this scope
make[2]: *** [basicset.o] Error 1
make[2]: Leaving directory `/home/yannick/brutalchess-0.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/yannick/brutalchess-0.5.2/src'
make: *** [all-recursive] Error 1

---

### Post by deci on 2008-06-13
> **PmDematagoda said:**
> Hasn't it finished successfully? From the log it looks like there are no errors.

Also this thread is moved to the General Help section.

look to what i posted secondly ...

---

