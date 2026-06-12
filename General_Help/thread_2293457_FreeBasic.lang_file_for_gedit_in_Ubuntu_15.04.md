---
title: "FreeBasic.lang file for gedit in Ubuntu 15.04"
date: 2015-09-05
forum: General Help
---

### Post by micahel-flower446 on 2015-09-05
Code language highlighting modes in gedit are governed by ".lang" files in "/usr/share/gtksourceview-3.0/language-specs/". I have edited the downloaded FreeBASIC.lang file from [ [http://forum.ubuntuusers.de/topic/syntax-datei-fuer-freebasic-mit-gedit/#post-2926767](http://forum.ubuntuusers.de/topic/syntax-datei-fuer-freebasic-mit-gedit/#post-2926767) ] and copied it to "/usr/share/gtksourceview-3.0/language-specs/FreeBASIC.lang" as a super-user. After I rebooted the computer, it did not work. What am I doing wrong?

```
<?xml version="1.0" encoding="UTF-8"?>
<!--
freebasic2.lang for GEDIT.  copy this file to /usr/share/gtksourceview-2.0/language-specs/
 
 5/2011 Martin Schlenker <schlenker.martin@gmx.de>
 20150824 Michael Flower <micahel.flower446@gmail.com>
   Edited to correct into current version of FreeBasic
   Changes reflect the FreeBasic manual 1.02.1
   This is should be copied to
     /usr/share/gtksourceview-3.0/language-specs/FreeBASIC.lang

This library is free software; you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation; either version 2 of the License, or
 (at your option) any later version.

 This program is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.

 You should have received a copy of the GNU General Public License
 along with this program; if not, write to the Free Software
 Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA


-->
<language id="freebasic" _name="FreeBASIC" version="2.0" _section="Sources">
  <metadata>
    <property name="mimetypes">text/x-freebasic</property>
    <property name="globs">*.bas</property>
    <property name="line-comment-start">''</property>
    <property name="block-comment-start">/'</property>
    <property name="block-comment-end">'/</property>
  </metadata>

  <styles>
    <style id="boolean" _name="Boolean value" map-to="def:boolean"/>
    <style id="comment" _name="Comment" map-to="def:comment"/>
    <style id="common-defines" _name="Common Defines" map-to="def:special-constant"/>
    <style id="decimal" _name="Decimal number" map-to="def:decimal"/>
    <style id="error" _name="Error" map-to="def:error"/>
    <style id="floating-point" _name="Floating point number" map-to="def:floating-point"/>
    <style id="function" _name="Function" map-to="def:function"/>
    <style id="hexadecimal" _name="Hexadecimal number" map-to="def:base-n-integer"/>
    <style id="included-file" _name="Included File" map-to="def:string"/>
    <style id="keyword" _name="Keyword" map-to="def:keyword"/>
    <style id="metacommand" _name="Metacommand" map-to="def:preprocessor"/>
    <style id="octal" _name="Octal number" map-to="def:base-n-integer"/>
    <style id="operator" _name="Operator" map-to="def:operator"/>
    <style id="preprocessor" _name="Preprocessor" map-to="def:preprocessor"/>
    <style id="signal-name" _name="Signal name" map-to="def:constant"/>
    <style id="standard-streams" _name="Standard Streams" style-ref="def:string"/>
    <style id="storage-class" _name="Storage Class" map-to="def:type"/>
    <style id="string" _name="String" map-to="def:string"/>
    <style id="type" _name="Data Type" map-to="def:type"/>
  </styles>

 <default-regex-options case-sensitive="false"/>

  <definitions>

<context id="line-comment" style-ref="comment" end-at-line-end="true">
      <start>''</start>
      <include>
        <context ref="def:in-line-comment"/>
      </include>
    </context>

  <context id="string" style-ref="string" end-at-line-end="true">
      <start>"</start>
      <end>"</end>
    </context>

   <context id="common-defines" style-ref="common-defines"> 
    <keyword>__DATE__</keyword>
    <keyword>__Date_iso__</keyword>
    <keyword>__Fb_64Bit__</keyword>
    <keyword>__FB_ARGC__</keyword>
    <keyword>__FB_ARGV__</keyword>
    <keyword>__FB_Arm__</keyword>
    <keyword>__FB_Asm__</keyword>
    <keyword>__FB_Backend__</keyword>
    <keyword>__FB_BIGENDIAN__</keyword>
    <keyword>__FB_BUILD_DATE__</keyword>
    <keyword>__FB_CYGWIN__</keyword>
    <keyword>__FB_DARWIN__</keyword>
    <keyword>__FB_DEBUG__</keyword>
    <keyword>__FB_DOS__</keyword>
    <keyword>__FB_ERR__</keyword>
    <keyword>__FB_Fpmode__</keyword>
    <keyword>__FB_Fpu__</keyword>
    <keyword>__FB_FREEBSD__</keyword> 
    <keyword>__FB_Gcc__</keyword>
    <keyword>__FB_LANG__</keyword>
    <keyword>__FB_LINUX__</keyword>
    <keyword>__FB_MAIN__</keyword>
    <keyword>__FB_MIN_VERSION__</keyword>
    <keyword>__FB_MT__</keyword>
    <keyword>__FB_NETBSD__</keyword>
    <keyword>__FB_OPENBSD__</keyword>
    <keyword>__FB_OPTION_BYVAL__</keyword>
    <keyword>__FB_OPTION_DYNAMIC__</keyword>
    <keyword>__FB_OPTION_ESCAPE__</keyword>
    <keyword>__FB_OPTION_EXPLICIT__</keyword>
    <keyword>__FB_Option_Gosub__</keyword>
    <keyword>__FB_OPTION_PRIVATE__</keyword>
    <keyword>__FB_OUT_DLL__</keyword>
    <keyword>__FB_OUT_EXE__</keyword>
    <keyword>__FB_OUT_LIB__</keyword>
    <keyword>__FB_OUT_OBJ__</keyword>
    <keyword>__FB_Pcos__</keyword>
    <keyword>__FB_SIGNATURE__</keyword>
    <keyword>__FB_SSE__</keyword>
    <keyword>__FB_Unix__</keyword>
    <keyword>__FB_Vectorize__</keyword>
    <keyword>__FB_VER_MAJOR__</keyword>
    <keyword>__FB_VER_MINOR__</keyword>
    <keyword>__FB_VER_PATCH__</keyword>
    <keyword>__FB_VERSION__</keyword>
    <keyword>__FB_WIN32__</keyword>
    <keyword>__FB_XBOX__</keyword>
    <keyword>__FILE__</keyword>
    <keyword>__FILE_NQ__</keyword>
    <keyword>__FUNCTION__</keyword>
    <keyword>__FUNCTION_NQ__</keyword>
    <keyword>__LINE__</keyword>
    <keyword>__PATH__</keyword>
    <keyword>__TIME__</keyword>
    </context>

   <context id="preprocessor" style-ref="preprocessor" case-sensitive="true" end-at-line-end="true"> 
    <keyword>#assert</keyword>
    <keyword>#define</keyword>
    <keyword>#else</keyword>
    <keyword>#elseif</keyword>
    <keyword>#endif</keyword>
    <keyword>#endmacro</keyword>
    <keyword>#error</keyword>
    <keyword>#if</keyword>
    <keyword>#ifdef</keyword>
    <keyword>#ifndef</keyword>
    <keyword>#inclib</keyword>
    <keyword>#include</keyword>
    <keyword>#lang</keyword>
    <keyword>#libpath</keyword>
    <keyword>#line</keyword>
    <keyword>#macro</keyword>
    <keyword>#pragma</keyword>
    <keyword>#print</keyword>
    <keyword>#undef</keyword>
   </context>

    <context id="metacommand" style-ref="metacommand">      
    <keyword>$Dynamic</keyword>
    <keyword>$Include</keyword>
    <keyword>$Static</keyword>
    <keyword>$Lang</keyword>
    </context>

    <context id="keywords" style-ref="keyword">      

    <!-- A -->
    <keyword>ABS</keyword>
    <keyword>ABSTRACT</keyword>
    <keyword>ACCESS</keyword>
    <keyword>ACOS</keyword>
    <keyword>ADD</keyword>
    <keyword>ALIAS</keyword>
    <keyword>ALLOCATE</keyword>
    <keyword>ALPHA</keyword>
    <keyword>AND</keyword>
    <keyword>ANDALSO</keyword>
    <keyword>ANY</keyword>
    <keyword>APPEND</keyword>
    <keyword>AS</keyword>
    <keyword>ASC</keyword>
    <keyword>ASIN</keyword>
    <keyword>ASM</keyword>
    <keyword>ASSERT</keyword>
    <keyword>ASSERTWARN</keyword>
    <keyword>ATAN2</keyword>
    <keyword>ATN</keyword>

    <!-- B -->
    <keyword>BASE</keyword>
    <keyword>BEEP</keyword>
    <keyword>BIN</keyword>
    <keyword>BINARY</keyword>
    <keyword>BIT</keyword>
    <keyword>BITRESET</keyword>
    <keyword>BITSET</keyword>
    <keyword>BLOAD</keyword>
    <keyword>BSAVE</keyword>
    <keyword>BYREF</keyword>
    <keyword>BYTE</keyword>
    <keyword>BYVAL</keyword>

    <!-- C -->
    <keyword>CALL</keyword>
    <keyword>CALLOCATE</keyword>
    <keyword>CASE</keyword>
    <keyword>CAST</keyword>
    <keyword>CBYTE</keyword>
    <keyword>CDBL</keyword>
    <keyword case-sensitive="true">cdecl</keyword>
    <keyword>CHAIN</keyword>
    <keyword>CHDIR</keyword>
    <keyword>CHR</keyword>
    <keyword>CINT</keyword>
    <keyword>CIRCLE</keyword>
    <keyword>CLASS</keyword>
    <keyword>CLEAR</keyword>
    <keyword>CLNG</keyword>
    <keyword>CLNGINT</keyword>
    <keyword>CLOSE</keyword>
    <keyword>CLS</keyword>
    <keyword>COLOR</keyword>
    <keyword>COMMAND</keyword>
    <keyword>COMMON</keyword>
    <keyword>CONDBROADCAST</keyword>
    <keyword>CONDCREATE</keyword>
    <keyword>CONDDESTROY</keyword>
    <keyword>CONDSIGNAL</keyword>
    <keyword>CONDWAIT</keyword>
    <keyword>CONST</keyword>
    <keyword>CONSTRUCTOR</keyword>
    <keyword>CONTINUE</keyword>
    <keyword>COS</keyword>
    <keyword>CPTR</keyword>
    <keyword>CSHORT</keyword>
    <keyword>CSIGN</keyword>
    <keyword>CSNG</keyword>
    <keyword>CSRLIN</keyword>
    <keyword>CUBYTE</keyword>
    <keyword>CUINT</keyword>
    <keyword>CULNG</keyword>
    <keyword>CULNGINT</keyword>
    <keyword>CUNSG</keyword>
    <keyword>CURDIR</keyword>
    <keyword>CUSHORT</keyword>
    <keyword>CUSTOM</keyword>
    <keyword>CVD</keyword>
    <keyword>CVI</keyword>
    <keyword>CVL</keyword>
    <keyword>CVLONGINT</keyword>
    <keyword>CVS</keyword>
    <keyword>CVSHORT</keyword>

    <!-- D -->
    <keyword>DATA</keyword>
    <keyword>DATE</keyword>
    <keyword>DATEADD</keyword>
    <keyword>DATEDIFF</keyword>
    <keyword>DATEPART</keyword>
    <keyword>DATESERIAL</keyword>
    <keyword>DATEVALUE</keyword>
    <keyword>DAY</keyword>
    <keyword>DEALLOCATE</keyword>
    <keyword>DECLARE</keyword>
    <keyword>DEFBYTE</keyword>
    <keyword>DEFDBL</keyword>
    <keyword case-sensitive="true">defined</keyword>
    <keyword>DEFINT</keyword>
    <keyword>DEFLNG</keyword>
    <keyword>DEFLONGINT</keyword>
    <keyword>DEFSHORT</keyword>
    <keyword>DEFSNG</keyword>
    <keyword>DEFSTR</keyword>
    <keyword>DEFUBYTE</keyword>
    <keyword>DEFUINT</keyword>
    <keyword>DEFULONGINT</keyword>
    <keyword>DEFUSHORT</keyword>
    <keyword>DELETE</keyword>
    <keyword>DESTRUCTOR</keyword>
    <keyword>DIM</keyword>
    <keyword>DIR</keyword>
    <keyword>DO</keyword>
    <keyword>DOUBLE</keyword>
    <keyword>DRAW</keyword>
    <keyword>DRAW STRING</keyword>
    <keyword>DYLIBFREE</keyword>
    <keyword>DYLIBLOAD</keyword>
    <keyword>DYLIBSYMBOL</keyword>
    <keyword>DYNAMIC</keyword>

    <!-- E -->
    <keyword>ELSE</keyword>
    <keyword>ELSEIF</keyword>
    <keyword>ENCODING</keyword>
    <keyword>END</keyword>
    <keyword>ENUM</keyword>
    <keyword>ENVIRON</keyword>
    <keyword>EOF</keyword>
    <keyword>EQV</keyword>
    <keyword>ERASE</keyword>
    <keyword>ERFN</keyword>
    <keyword>ERL</keyword>
    <keyword>ERMN</keyword>
    <keyword>ERR</keyword>
    <keyword>ERROR</keyword>
    <keyword>ESCAPE</keyword>
    <keyword>EVENT</keyword>
    <keyword>EXEC</keyword>
    <keyword>EXEPATH</keyword>
    <keyword>EXIT</keyword>
    <keyword>EXP</keyword>
    <keyword>EXPLICIT</keyword>
    <keyword>EXPORT</keyword>
    <keyword>EXTERN</keyword>

    <!-- F -->
    <keyword>FIELD</keyword>
    <keyword>FILEATTR</keyword>
    <keyword>FILECOPY</keyword>
    <keyword>FILEDATETIME</keyword>
    <keyword>FILEEXISTS</keyword>
    <keyword>FILELEN</keyword>
    <keyword>FIX</keyword>
    <keyword>FLIP</keyword>
    <keyword>FOR</keyword>
    <keyword>FORMAT</keyword>
    <keyword>FRAC</keyword>
    <keyword>FRE</keyword>
    <keyword>FREEFILE</keyword>
    <keyword>FUNCTION</keyword>

    <!-- G -->
    <keyword>GET</keyword>
    <keyword>GETJOYSTICK</keyword>
    <keyword>GETKEY</keyword>
    <keyword>GETMOUSE</keyword>
    <keyword>GOSUB</keyword>
    <keyword>GOTO</keyword>

    <!-- H -->
    <keyword>HEX</keyword>
    <keyword>HIBYTE</keyword>
    <keyword>HIWORD</keyword>
    <keyword>HOUR</keyword>

    <!-- I -->
    <keyword>IF</keyword>
    <keyword>IIF</keyword>
    <keyword>IMAGECONVERTROW</keyword>
    <keyword>IMAGECREATE</keyword>
    <keyword>IMAGEDESTROY</keyword>
    <keyword>IMAGEINFO</keyword>
    <keyword>IMP</keyword>
    <keyword>IMPLEMENTS</keyword>
    <keyword>IMPORT</keyword>
    <keyword>INKEY</keyword>
    <keyword>INP</keyword>
    <keyword>INPUT</keyword>
    <keyword>INPUT$</keyword>
    <keyword>INSTR</keyword>
    <keyword>INSTRREV</keyword>
    <keyword>INT</keyword>
    <keyword>INTEGER</keyword>
    <keyword>IS</keyword>
    <keyword>ISDATE</keyword>
    <keyword>ISREDIRECTED</keyword>

    <!-- J -->

    <!-- K -->
    <keyword>KILL</keyword>

    <!-- L -->
    <keyword>LBOUND</keyword>
    <keyword>LCASE</keyword>
    <keyword>LEFT</keyword>
    <keyword>LEN</keyword>
    <keyword>LET</keyword>
    <keyword>LIB</keyword>
    <keyword>LINE</keyword>
    <keyword>LOBYTE</keyword>
    <keyword>LOC</keyword>
    <keyword>LOCAL</keyword>
    <keyword>LOCATE</keyword>
    <keyword>LOCK</keyword>
    <keyword>LOF</keyword>
    <keyword>LOG</keyword>
    <keyword>LONG</keyword>
    <keyword>LONGINT</keyword>
    <keyword>LOOP</keyword>
    <keyword>LOWORD</keyword>
    <keyword>LPOS</keyword>
    <keyword>LPRINT</keyword>
    <keyword>LPT</keyword>
    <keyword>LSET</keyword>
    <keyword>LTRIM</keyword>

    <!-- M -->
    <keyword>MID</keyword>
    <keyword>MINUTE</keyword>
    <keyword>MKD</keyword>
    <keyword>MKDIR</keyword>
    <keyword>MKI</keyword>
    <keyword>MKL</keyword>
    <keyword>MKLONGINT</keyword>
    <keyword>MKS</keyword>
    <keyword>MKShort</keyword>
    <keyword>MOD</keyword>
    <keyword>MONTH</keyword>
    <keyword>MONTHNAME</keyword>
    <keyword>MULTIKEY</keyword>
    <keyword>MUTEXCREATE</keyword>
    <keyword>MUTEXDESTROY</keyword>
    <keyword>MUTEXLOCK</keyword>
    <keyword>MUTEXUNLOCK</keyword>

    <!-- N -->
    <keyword>NAKED</keyword>
    <keyword>NAME</keyword>
    <keyword>NAMESPACE</keyword>
    <keyword>NEW</keyword>
    <keyword>NEXT</keyword>
    <keyword>NOGOSUB</keyword>
    <keyword>NOKEYWORD</keyword>
    <keyword>NOT</keyword>
    <keyword>NOW</keyword>

    <!-- O -->
    <keyword>OBJECT</keyword>
    <keyword>OCT</keyword>
    <keyword>OFFSETOF</keyword>
    <keyword>ON</keyword>
    <keyword>ONCE</keyword>
    <keyword>OPEN</keyword>
    <keyword>OPERATOR</keyword>
    <keyword>OPTION</keyword>
    <keyword>OR</keyword>
    <keyword>ORELSE</keyword>
    <keyword>OUT</keyword>
    <keyword>OUTPUT</keyword>
    <keyword>OVERLOAD</keyword>
    <keyword>OVERRIDE</keyword>

    <!-- P -->
    <keyword>PAINT</keyword>
    <keyword>PALETTE</keyword>
    <keyword case-sensitive="true">pascal</keyword>
    <keyword>PCOPY</keyword>
    <keyword>PEEK</keyword>
    <keyword>PMAP</keyword>
    <keyword>POINT</keyword>
    <keyword>POINTCOORD</keyword>
    <keyword>POINTER</keyword>
    <keyword>POKE</keyword>
    <keyword>POS</keyword>
    <keyword>PRESERVE</keyword>
    <keyword>PRESET</keyword>
    <keyword>PRINT</keyword>
    <keyword>PRIVATE</keyword>
    <keyword>PROCPTR</keyword>
    <keyword>PROPERTY</keyword>
    <keyword>PROTECTED</keyword>
    <keyword>PSET</keyword>
    <keyword>PTR</keyword>
    <keyword>PUBLIC</keyword>
    <keyword>PUT</keyword>

    <!-- Q -->

    <!-- R -->
    <keyword>RANDOM</keyword>
    <keyword>RANDOMIZE</keyword>
    <keyword>READ</keyword>
    <keyword>REALLOCATE</keyword>
    <keyword>REDIM</keyword>
    <keyword>REM</keyword>
    <keyword>RESET</keyword>
    <keyword>RESTORE</keyword>
    <keyword>RESUME</keyword>
    <keyword>RETURN</keyword>
    <keyword>RGB</keyword>
    <keyword>RGBA</keyword>
    <keyword>RIGHT</keyword>
    <keyword>RMDIR</keyword>
    <keyword>RND</keyword>
    <keyword>RSET</keyword>
    <keyword>RTRIM</keyword>
    <keyword>RUN</keyword>

    <!-- S -->
    <keyword>SADD</keyword>
    <keyword>SCOPE</keyword>
    <keyword>SCREEN</keyword>
    <keyword>SCREENCONTROL</keyword>
    <keyword>SCREENCOPY</keyword>
    <keyword>SCREENEVENT</keyword>
    <keyword>SCREENGLPROC</keyword>
    <keyword>SCREENINFO</keyword>
    <keyword>SCREENLIST</keyword>
    <keyword>SCREENLOCK</keyword>
    <keyword>SCREENPTR</keyword>
    <keyword>SCREENRES</keyword>
    <keyword>SCREENSET</keyword>
    <keyword>SCREENSYNC</keyword>
    <keyword>SCREENUNLOCK</keyword>
    <keyword>SECOND</keyword>
    <keyword>SEEK</keyword>
    <keyword>SELECT</keyword>
    <keyword>SETDATE</keyword>
    <keyword>SETENVIRON</keyword>
    <keyword>SETMOUSE</keyword>
    <keyword>SETTIME</keyword>
    <keyword>SGN</keyword>
    <keyword>SHARED</keyword>
    <keyword>SHELL</keyword>
    <keyword>SHL</keyword>
    <keyword>SHORT</keyword>
    <keyword>SHR</keyword>
    <keyword>SIN</keyword>
    <keyword>SINGLE</keyword>
      <keyword>SIZEOF</keyword>
    <keyword>SLEEP</keyword>
    <keyword>SPACE</keyword>
    <keyword>SPC</keyword>
    <keyword>SQR</keyword>
    <keyword>STATIC</keyword>
    <keyword>STDCALL</keyword>
    <keyword>STEP</keyword>
    <keyword>STICK</keyword>
    <keyword>STOP</keyword>
    <keyword>STR</keyword>
    <keyword>STRIG</keyword>
    <keyword>STRING</keyword>
    <keyword>STRPTR</keyword>
    <keyword>SUB</keyword>
    <keyword>SWAP</keyword>
    <keyword>SYSTEM</keyword>

    <!-- T -->
    <keyword>TAB</keyword>
    <keyword>TAN</keyword>
    <keyword>THEN</keyword>
    <keyword>THIS</keyword>
    <keyword>THREADCALL</keyword>
    <keyword>THREADCREATE</keyword>
    <keyword>THREADDETACH</keyword>
    <keyword>THREADWAIT</keyword>
    <keyword>TIME</keyword>
    <keyword>TIMER</keyword>
    <keyword>TIMESERIAL</keyword>
    <keyword>TIMEVALUE</keyword>
    <keyword>TO</keyword>
    <keyword>TRANS</keyword>
    <keyword>TRIM</keyword>
    <keyword>TYPE</keyword>
    <keyword>TYPEOF</keyword>

    <!-- U -->
    <keyword>UBOUND</keyword>
    <keyword>UBYTE</keyword>
    <keyword>UCASE</keyword>
    <keyword>UINTEGER</keyword>
    <keyword>ULONG</keyword>
    <keyword>ULONGINT</keyword>
    <keyword>UNION</keyword>
    <keyword>UNLOCK</keyword>
    <keyword>UNSIGNED</keyword>
    <keyword>UNTIL</keyword>
    <keyword>USHORT</keyword>
    <keyword>USING</keyword>

    <!-- V -->
    <keyword>VA_ARG</keyword>
    <keyword>VA_FIRST</keyword>
    <keyword>VA_NEXT</keyword>
    <keyword>VAL</keyword>
    <keyword>VALINT</keyword>
    <keyword>VALLNG</keyword>
    <keyword>VALUINT</keyword>
    <keyword>VALULNG</keyword>
    <keyword>VAR</keyword>
    <keyword>VARPTR</keyword>
    <keyword>VIEW</keyword>
    <keyword>VIRTUAL</keyword>

    <!-- W -->
    <keyword>WAIT</keyword>
    <keyword>WBIN</keyword>
    <keyword>WCHR</keyword>
    <keyword>WEEKDAY</keyword>
    <keyword>WEEKDAYNAME</keyword>
    <keyword>WEND</keyword>
    <keyword>WHEX</keyword>
    <keyword>WHILE</keyword>
    <keyword>WIDTH</keyword>
    <keyword>WINDOW</keyword>
    <keyword>wINDOWTITLE</keyword>
    <keyword>WINPUT</keyword>
    <keyword>WITH</keyword>
    <keyword>WOCT</keyword>
    <keyword>WRITE</keyword>
    <keyword>WSPACE</keyword>
    <keyword>WSTR</keyword>
    <keyword>WSTRING</keyword>

    <!-- X -->
    <keyword>XOR</keyword>

    <!-- Y -->
    <keyword>YEAR</keyword>

    <!-- Z -->
    <keyword>ZSTRING</keyword>
   </context>


    <context id="floating-point" style-ref="floating-point">
      <match extended="true">
        (?&lt;![\w\.])
        ([0-9]+[Ee][-+]?[0-9]+|
         ([0-9]*\.[0-9]+|[0-9]+\.)([Ee][-+]?[0-9]+)?)
        [i]?
        (?![\w\.])
      </match>
    </context>

    <context id="freebasic">
      <include>
        <context ref="def:comment"/>
        <context ref="def:floating-point"/>
        <context ref="def:function"/>
        <context ref="def:keywords"/>
        <context ref="def:operator"/>
        <context ref="def:preprocessor"/>
        <context ref="def:shell-like-comment"/>
        <context ref="def:single-quoted-string"/>
        <context ref="def:special-constant"/>
        <context ref="def:string"/>
        <context ref="def:type"/>
      </include>

    </context>
   
  </definitions>

</language>
```

---

