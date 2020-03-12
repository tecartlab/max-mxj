# max-mxj
[![Build Status](https://travis-ci.com/Cycling74/max-mxj.svg?token=GAmnsUEo9aYasSF5pz8q&branch=master)](https://travis-ci.com/Cycling74/max-mxj)
[![Build status](https://ci.appveyor.com/api/projects/status/gp3t8xshfsjbmdcy?svg=true)](https://ci.appveyor.com/project/c74/max-mxj)

The mxj/mxj~ objects for authoring objects in Max using Java.


## Continuous Integration

Builds can be downloaded from [S3](https://s3-us-west-2.amazonaws.com/cycling74-ci/index.html?prefix=max-mxj/)

Use the badges above to go directly to the CI services.


## To build (Mac)

* `mkdir build`
* `cd build`
* `cmake -G Xcode ..`
* `cmake --build .` (or open the Xcode project in this build folder and build there)
* `cmake --build . --config Release`


## To build (Windows)
Download the Windows x86 openJava SE Development Kit 13 (from http://jdk.java.net/13/ and install it in the default location (C:\Program Files\Java). Rename if needed to 'C:\Program Files\Java\jdk-13.0.2'.

Open the mxj or mxj~ project in Visual Studio 2013

When using Visual Studio Community 2017 you need to download an older sdk: https://developer.microsoft.com/de-de/windows/downloads/sdk-archive/

and the atl library is in this ISO: https://download.microsoft.com/download/4/A/2/4A25C7D5-EFBE-4182-B6A9-AE6850409A78/GRMWDK_EN_7600_1.ISO



## MXJ rules for searching for Java:
On OSX, it searches in that order: embeded JRE, on system JDK, on system JRE
The search for an embeded JRE is done in the application, in the folder MyApp.app/Contents/Resources/C74/packages/max-mxj/jre
The JRE must have the structure :
jre/Contents/Home
jre/Contents/MacOS
jre/Contents/Plugins
jre/Contents/Resources
jre/Contents/Frameworks

The JRE can be found here after installing a java internet plugin:
"/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/"
Copy that folder and rename it "jre"

On Windows, it searches in that order: embeded JRE, on system JDK, on system JRE
The search for an embeded JRE is done in the application, it must be a folder named "jre" placed in the same folder as the application .exe

Make sure the following registry entries are set:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft]

[HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\JDK]
"CurrentVersion"="1.13"

[HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\JDK\1.13]
"JavaHome"="C:\\Program Files\\Java\\jdk-13.0.2"

[HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\JRE]
"CurrentVersion"="1.13"

[HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\JRE\1.13]
"RuntimeLib"="C:\\Program Files\\Java\\jdk-13.0.2\\bin\\server\\jvm.dll"
"JavaHome"="C:\\Program Files\\Java\\jdk-13.0.2"
```

you can copy-paste this lines into a notepad and save the file with a .reg extension and execute it. just make sure all the references are accurate, otherwise mxj will not find the jvm.

If you install the older JDK the registries are set to different subfolder:

 you need to add the above paths (with 'JRE') otherwise this build of mxj will not find the jvm.
