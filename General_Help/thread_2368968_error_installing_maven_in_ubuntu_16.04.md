---
title: "error installing maven in ubuntu 16.04"
date: 2017-08-17
forum: General Help
---

### Post by davidtuti2 on 2017-08-17
Hi,
I'm trying to install maven in ubuntu 16.04. and it gives me an error:

```
sudo apt-get install maven
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 libmagickwand-6.q16-2 : Depende: imagemagick-common (= 8:6.8.9.9-7ubuntu5.9) pero 8:6.8.9.9-7ubuntu5.3 va a ser instalado
 maven : Depende: default-jre-headless (>= 2:1.7) pero no va a instalarse o
                  java7-runtime-headless
         Depende: libmaven3-core-java (= 3.3.9-3) pero no va a instalarse
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).


```

Ahy help? Many Thanks!

---

### Post by shridhar-kapshikar on 2017-08-17
You can install the Maven by adding the repository or downloading the tar ball.

Please share the output of below command. 
```
[COLOR=black][FONT=Consolas]$ sudo apt-cache search maven[/FONT][/COLOR]

```

---

### Post by davidtuti2 on 2017-08-17
Output:
> sudo apt-cache search maven
[sudo] password for david: 
antlr3-maven-plugin - Maven plugin for ANTLR 3
antlr3.2-maven-plugin - Maven plugin for ANTLR 3.2
bnd - tool to create and diagnose OSGi bundles
libdoxia-java-doc - Documentation for libdoxia-java
libdoxia-maven-plugin-java - Maven plugin for Doxia
libmaven-antrun-plugin-java - Maven AntRun Plugin
libmaven-archiver-java - Archiver component for Maven
libmaven-archiver-java-doc - Archiver component for Maven - API documentation
libmaven-assembly-plugin-java - Maven Assembly Plugin
libmaven-bundle-plugin-java - Maven plugin to handle artifact OSGi metadata
libmaven-bundle-plugin-java-doc - Maven plugin to handle artifact OSGi metadata - documentation
libmaven-clean-plugin-java - Maven clean plugin
libmaven-clean-plugin-java-doc - Maven clean plugin - API documentation
libmaven-common-artifact-filters-java - Maven Common Artifact Filters
libmaven-common-artifact-filters-java-doc - Documentation for Maven Common Artifact Filters
libmaven-compiler-plugin-2.5-java - Maven Compiler plugin
libmaven-compiler-plugin-2.5-java-doc - Documentation for Maven Compiler Plugin
libmaven-compiler-plugin-java - Maven Compiler plugin
libmaven-compiler-plugin-java-doc - Documentation for Maven Compiler Plugin
libmaven-dependency-analyzer-java - Maven Dependency Analyzer
libmaven-dependency-plugin-java - Maven Dependency Plugin
libmaven-dependency-tree-java - Maven Dependency Tree
libmaven-dependency-tree-java-doc - Documentation for Maven Dependency Tree
libmaven-deploy-plugin-java - Maven Deploy plugin
libmaven-docck-plugin-java - Maven Documentation Checker Plugin
libmaven-doxia-tools-java - utilities for integrating Doxia in Maven
libmaven-doxia-tools-java-doc - Documentation for Maven Doxia Integration Tools
libmaven-ear-plugin-java - Maven EAR Plugin
libmaven-ejb-plugin-java - Maven EJB Plugin
libmaven-embedder-java - Maven Embedder
libmaven-embedder-java-doc - Documentation for Maven Embedder
libmaven-file-management-java - Maven File Management API
libmaven-file-management-java-doc - Documentation for Maven File Management API
libmaven-filtering-java - Maven Filtering
libmaven-install-plugin-java - Maven install plugin
libmaven-install-plugin-java-doc - Documentation for Maven Install Plugin
libmaven-invoker-java - Maven Invoker
libmaven-invoker-plugin-java - Maven Invoker Plugin
libmaven-jar-plugin-java - Maven Jar Plugin
libmaven-jar-plugin-java-doc - Documentation for Maven Jar Plugin
libmaven-javadoc-plugin-java - Maven Javadoc Plugin
libmaven-parent-java - Maven metadata for Apache Maven itself
libmaven-plugin-testing-java - Maven Plugin Testing
libmaven-plugin-testing-java-doc - Documentation for Maven Plugin Testing
libmaven-plugin-tools-java - Maven Plugin Tools
libmaven-project-info-reports-plugin-java - Maven Project Info Reports Plugin
libmaven-reporting-impl-java - Maven Reporting API Implementation
libmaven-reporting-impl-java-doc - Documentation for Maven Reporting API Implementation
libmaven-repository-builder-java - Maven Repository Builder
libmaven-repository-builder-java-doc - Documentation for Maven Repository Builder
libmaven-resources-plugin-java - Maven resources plugin
libmaven-scm-java-doc - Maven SCM - Common API for SCM operations (Documentation)
libmaven-shade-plugin-java - Maven shade plugin
libmaven-shared-io-java - Maven API for I/O support
libmaven-shared-io-java-doc - Documentation for Maven API for I/O support
libmaven-site-plugin-java - Maven Site Plugin for generating a site
libmaven-verifier-java - Maven Verifier Component
libmaven-verifier-java-doc - Documentation for Maven Verifier Component
libmaven-war-plugin-java - Maven WAR Plugin
libmaven2-core-java - Bibliotecas del núcleo para Maven2
libmaven2-core-java-doc - Documentación API para Maven2
libmaven3-core-java - Core libraries for Maven 3
libmodello-java-doc - Data Model toolkit in use by the Maven 2 Project (documentation)
libnetbeans-cvsclient-java - Biblioteca cliente de NetBeans CVS
libsurefire-java - Surefire test framework for Java
maven - Java software project management and comprehension tool
antlr3-gunit-maven-plugin - Maven plugin for gUnit, a unit test framework for ANTLR grammars
antlr3.2-gunit-maven-plugin - Maven plugin for gUnit, a unit test framework for ANTLR grammars
antlr4-maven-plugin - Maven plugin for ANTLR 4
elpa-projectile - project interaction library for Emacs
gradle-debian-helper - Helper tools for building Debian packages with Gradle
gradle-propdeps-plugin - Gradle plugin enhancing the Maven integration
ivy-debian-helper - Helper tools for building Debian packages with Ivy
jruby-maven-plugins - Maven plugins to handle Ruby gems in a Maven compatible way
libaccess-modifier-checker-java - Maven plugin for custom access modifier checking
libaccess-modifier-checker-java-doc - Documentation for libaccess-modifier-checker-java
libactivemq-protobuf-java - ActiveMQ Protocol Buffers Maven plugin
libactivemq-protobuf-java-doc - ActiveMQ Protocol Buffers Maven plugin - documentation
libaether-java - Library to handle Java artifact repositories
libanimal-sniffer-java - JDK/API verification tools
libantlr-maven-plugin-java - Maven ANTLR Plugin
libapache-pom-java - Maven metadata for all Apache Software projects
libaspectj-maven-plugin-java - AspectJ compiler Maven Plugin
libavro-maven-plugin-java - Apache Avro Maven plugin
libbridge-method-injector-java - Evolve Java classes without breaking compatibility
libbridge-method-injector-java-doc - Documentation for Bridge Method Injector
libbuild-helper-maven-plugin-java - Build Helper Maven Plugin
libbuild-helper-maven-plugin-java-doc - Documentation for Build Helper Maven Plugin
libclirr-maven-plugin-java - Clirr Maven Plugin
libclojure-maven-plugin-java - Clojure plugin for Maven
libcommons-parent-java - Maven metadata for Apache Commons project
libdoxia-core-java - Doxia content generation framework (core)
libdoxia-java - Doxia content generation framework (modules)
libdoxia-sitetools-java - Extension package of the content generation framework Doxia
libdoxia-sitetools-java-doc - Documentation for Doxia Sitetools
libeclipse-aether-java - Library to handle Java artifact repositories
libfreehep-chartableconverter-plugin-java - FreeHEP Character Table Converter
libjackrabbit-java - content repository implementation (JCR API)
libjarjar-maven-plugin-java - Maven plugin to repackage third-party jars
libjarjar-maven-plugin-java-doc - Maven plugin to repackage third-party jars - documentation
libjavacc-maven-plugin-java - maven plugin which uses JavaCC to process JavaCC grammar files
libjdeb-java - utility to construct Debian packages from Ant or Maven
libjdependency-java - Java library analyzing class level dependencies
libjellydoc-java - Library for helping generate Jelly taglib documentation
libjellydoc-java-doc - Documentation for libjellydoc-java
libjglobus-parent-java - Globus Java - parent pom file
libmaven-ant-tasks-java - use Maven's artifact handling features from Ant
libmaven-antrun-extended-plugin-java - Extended integration between Maven and Ant
libmaven-antrun-extended-plugin-java-doc - Documentation for extended integration between Maven and Ant
libmaven-cobertura-plugin-java - Maven Cobertura Plugin
libmaven-enforcer-plugin-java - Maven build rule execution framework
libmaven-exec-plugin-java - Maven Exec Plugin
libmaven-indexer-java - Maven :: Indexer
libmaven-processor-plugin-java - Maven plugin to process annotations for Java 6 at compile time
libmaven-scm-java - Maven SCM - Common API for SCM operations (Core API)
libmaven-scm-providers-java - Maven SCM - Common API for SCM operations (Providers)
libmaven-script-interpreter-java - Maven Script Interpreter
libmaven-shared-incremental-java - Maven incremental build utilities
libmaven-shared-incremental-java-doc - Maven incremental build utilities (documentation)
libmaven-shared-jar-java - Maven JAR Utilities
libmaven-shared-jar-java-doc - Documentation for Maven JAR Utilities
libmaven-shared-utils-java - Replacement for plexus-utils in Maven
libmaven-shared-utils-java-doc - Replacement for plexus-utils in Maven (documentation)
libmaven-source-plugin-java - Maven Source Plugin
libmaven-stapler-plugin-java - Maven plugin for developing stapler applications
libmodello-java - Data Model toolkit in use by the Maven 2 Project
libmodello-maven-plugin-java - Modello Maven Plugin enables the use of Modello in Maven builds
libmodello-maven-plugin-java-doc - Documentation for Modello Maven Plugin
libmunge-maven-plugin-java - Maven plugin to pre-process Java code
libmunge-maven-plugin-java-doc - Maven plugin to pre-process Java code - documentation
libnetty-tcnative-java - Tomcat native fork for Netty
libnetty-tcnative-jni - Tomcat native fork for Netty (JNI library)
libparanamer-maven-plugin-java - Paranamer Maven Plugin
libplexus-cipher-java - Plexus Cipher Component used by Maven
libplexus-cipher-java-doc - Documentation for Plexus Cipher Component used by Maven
libplexus-component-metadata-java - Component Metadata Maven plugin for Plexus
libplexus-interpolation-java - Plexus Interpolation API
libplexus-interpolation-java-doc - Documentation for Plexus Interpolation API
libplexus-io-java - Plexus IO Components
libplexus-maven-plugin-java - Maven plugin for the Plexus Component Descriptor Creator
libplexus-maven-plugin-java-doc - Documentation for Plexus Maven Plugin
libplexus-sec-dispatcher-java - Plexus Security Dispatcher Component used by Maven
libpolyglot-maven-java - modules to enable Maven usage in others JVM languages
libpolyglot-maven-java-doc - modules to enable Maven usage in others JVM languages - docs
libproperties-maven-plugin-java - Maven Plugin to read and write property files from mojo.codehaus.org
libproperties-maven-plugin-java-doc - Documentation for Properties Maven Plugin
libreplacer-java - Maven plugin to replace tokens in a given file with a value
libsisu-ioc-java - JSR 330 container and OSGi/Plexus adapter
libsisu-maven-plugin-java - Manage Sisu components and applications
libsisu-plexus-java - Plexus adapter for the Sisu dependency injection container
libtomcat-maven-plugin-java - Tomcat Maven plugin
libwagon-java - tools to manage Maven artifacts and deployment
libwagon-java-doc - tools to manage Maven artifacts and deployment - documentation
libwagon2-java - resources' transport abstraction that is used in Maven
libxml-maven-plugin-java - Maven XML Plugin
libxmlbeans-maven-plugin-java - Maven XMLBeans Plugin
libxmlbeans-maven-plugin-java-doc - Documentation for Maven XMLBeans Plugin
maven-ant-helper - helper scripts for building Maven components with ant
maven-debian-helper - Helper tools for building Debian packages with Maven
maven-repo-helper - Helper tools for including Maven metadata in Debian packages
testng - testing framework for Java



---

### Post by vocx on 2017-08-17
> **davidtuti2 said:**
> Hi,
I'm trying to install maven in ubuntu 16.04. and it gives me an error:

```
sudo apt-get install maven
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 libmagickwand-6.q16-2 : Depende: imagemagick-common (= 8:6.8.9.9-7ubuntu5.9) pero 8:6.8.9.9-7ubuntu5.3 va a ser instalado
 maven : Depende: **default-jre-headless** (>= 2:1.7) pero no va a instalarse o
                  **java7-runtime-headless**
         Depende: **libmaven3-core-java** (= 3.3.9-3) pero no va a instalarse
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).


```

Ahy help? Many Thanks!
Did you read what it tells you?

You should install the dependencies that it needs to correctly install.
```

sudo apt install java7-runtime-headless
sudo apt install libmaven3-core-java

```

If that doesn't work, it also tells you to use the force option
```

sudo apt-get -f install

```

If that still doesn't work, you may be having a problem with your "sources.list" file. Did you add a particular repository in your "/etc/apt/sources.list"? This may cause you some problems, so you should verify this.

---

