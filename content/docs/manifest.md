title: Application Manifest
---

# (ST2.1/3.0) Application Manifest - v1.2.1.1

# **Application Manifest**

The following table shows the configuration document
file information in the widget package structure.  
Almost optional fields as well as the mandatory ones are compliant to
[[W3C widget configuration](https://www.w3.org/TR/widgets/)]
specifications. In this document is mainly described Widget Attributes
and Element which are supported by Application Framework extension. This
document also will be helpful to authors to edit manifest with Config
Manifest editor through Obigo Studio.

This document is available for below version of the Application Framework.

  - *ST2.1 ObigoAF\_v1.4.5*
  - *ST3.0 ObigoAF\_v1.6.15*

## Table of Contents


  - [1. Namespace](#id-namespace)
  - [2. Widget Element and its Attributes](#id-widget-element-and-its-attributes)

<!-- end list -->

  - [2.1 Attributes](#id-attributes)
  - [2.2 The <name\> Element](#id-name-element)
  - [2.3 The <description\> Element](#id-description-element)
  - [2.4 The <author\> Element](#id-author-element)
  - [2.5 The <license\> Element](#id-license-element)
  - [2.6 The <icon\> Element](#id-icon-element)
  - [2.7 The <content\> Element](#id-content-element)
  - [2.8 The <feature\> Element](#id-feature-element)
  - [2.9 The <access\> Element](#id-access-element)
  - [2.10 The <thumbnail\> Element](#id-thumbnail-element)
  - [2.11 The <depend-service\> Element](#id-depend-service-element)
  - [2.12 The <gadgets\> Element](#id-gadgets-element)
  - [2.13 The <intent\> Element](#id-intent-element)
  - [2.14 The <meta-data\> Element](#id-meta-data-element)


| No  | **Terms**             | **Description**                             |
|-----| ----------------------| --------------------------------------------|
| [1] | Application Framework | Obigo Application Framework                 |
| [2] | AF Extension Element  | Extension Element For Application Framework |
 

-----

## Widget Configuration

## 1. Namespace <a id="id-namespace"></a>

The widget namespace URI for a [[W3C Widget configuration document](https://www.w3.org/TR/widgets/#configuration-document-0)] is `<http://www.w3.org/ns/widgets>`[[XMLNS](https://www.w3.org/TR/widgets/#xmlns)]

## 2. Widget Element and its Attributes <a id="id-widget-element-and-its-attributes"></a>

The `widget` element is the root element of a
[[configuration document](https://www.w3.org/TR/widgets/#configuration-document-0)].

### **2.1 Attributes <a id="id-attributes"></a>**

#### **The `id` Attribute**

An IRI attribute that denotes an identifier for the widget. It's **mandatory** for authors to use
id attribute with a widget element.  
This will be automatically set by Obigo Studio.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
</widget>
```

#### **The `version` Attribute**

The version of an application : “\[0-9\].\[0-9\].\[0-9\]”. It's **mandatory** for authors to use version attribute with the widget element.

Each part of version number means major, miner and patch version. This version is also used for the widget package update
through SOTA.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
</widget>
```

#### **The `viewmodes` Attribute**

A keyword denotes the author's preferred visual view mode. It implies that the author expects the user agent to select an appropriate viewmode for an application.

The viewmodes feature is based on [[W3C view-mode](https://dev.w3.org/2006/waf/widgets-vmmf/)]. The only supported view-mode for AIVI is below.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>  
</widget>
```

  - fullscreen - Default view mode. Use the entire area assigned to the browser as the app display area.  
    This view mode is available to take 'transparent' mode together.

> viewmodes="fullscreen|transparent"


transparent : Provide transparent view. HTML Application has default
background color as black. If view mode set with 'transparent', then an
application displays background color as transparent unless author set
background color through CSS.  
This view mode may be useful for displaying different two applications
running in overlap.

  - service - Apps that run only in the background.
    Rendering does not work even if the HTML is manipulated and it does not switch to the foreground.

> viewmodes="service"

#### **The `defaultlocale` Attribute**

A language attribute that specifies the author's preferred local for an application. Its intended use is to provide a fallback in case the user agent cannot match any of an application's localized content to user agent locals list or in case the author has not provided any un-localized content.

#### **The `autostart` Attribute**

A auto start-able attribute that specifies the author's preferred an application start automatically.

#### **The `killable` Attribute**

A Killable priority attribute that specifies the author's preferred an application killable. If an application has any dependency with HMI. It's should set to 'false'.

  - true - Connected services has no dependency with HMI. It's set default.
  - false - Contend service has no dependency with HMI. If it's set to 'false', an application shall be killed lower priority by "Out Of Memory"

#### **The `group` Attribute**

A life cycle attribute that specifies the author's preferred life-cycle group for an application.

  - utility - Application that is totally autonomous and which do not have any control group. However, these applications can be stopped by user and "Out Of Memory". It's set default.
  - technical - Application that runs in background in the Application Framework and that can not be removed by the user.
  - system - Technical application that shall be killed at last in a case of "Out Of Memory" due to play a significant role on the framework
  - permanent - Application that can not be uninstalled by the user. However, these applications can be uninstalled by factory reset.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>    
</widget>
```
 

### **2.2 The < name > Element <a id="id-name-element"></a>**

The name element represents the full human-readable name for an application that is used in the framework.

#### **2.2.1 Attribute**

##### **The `short` Attribute**

The short-cut text attribute that specifies the author's preferred title on AppLauncher.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <name short="app1"> Application_test </name>
</widget>
```

### **2.3 The < description > Element**<a id="id-description-element"></a>

The description element represents a human-readable description of an application.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <description> Home for various applications. You can enjoy and explore the variety of apps in your car! </description>
</widget>
```
 
### **2.4 The < author > Element <a id="id-author-element"></a>**

An author element represents people or an organization attributed with the creation of an application.

#### **2.4.1 Attribute**

##### **The `href` Attribute**

An IRI attribute whose value represents an IRI that the author associates with himself or herself (e.g., a homepage, a profile on a social network, etc.).

##### **The `email` Attribute**

A string attribute that represents an email address associated with the author.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <author href="http://obigo.com" email="obigo@[obigo.com](http://obigo.com)"> Obigo Inc. </author>
</widget>
```

### **2.5 The < license > Element <a id="id-license-element"></a>**

The license element represents a software license, which includes, for example, a usage agreement, redistribution statement, and/or a copyright license terms under which the content of the widget package is provided.

#### **2.5.1 Attribute**

##### **The `href` Attribute**

A valid IRI or a valid path that points to a representation of a software and/or content license.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <license href="http://obigo.com" > 
        Example license (based on MIT License)
        Copyright (c) 2009 Obigo Inc.
        THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
        MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
        IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
        CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
        INSULT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
        SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
     </license>
</widget>
```


### **2.6 The < icon > Element <a id="id-icon-element"></a>**

The icon element represents a custom icon for an application.

#### **2.6.1 Attribute**

##### **The `src` Attribute**

A path attribute that points to a file inside the widget package, the author's preferred icon with short name on AppLauncher.

##### **The `width` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred width for the icon.

###### **The `height` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred height for the icon.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <icon src="icon.png" > </icon>
</widget>
```
 

### **2.7 The < content > Element <a id="id-content-element"></a>**

The content element is used by an author to declare which custom start file the user agent is expected to use when it instantiates an application.

#### **2.7.1 Attribute**

##### **The `src` Attribute**

A path attribute that allows an author to point to a file within the widget package.</span>

##### **The `type` Attribute**

A media type attribute that indicates the media type of the file referenced by the src attribute.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <content src="index.html" type="text/html"> </content>
</widget>
```


### **2.8 The < feature > Element <a id="id-feature-element"></a>**

A feature is a URI identifiable runtime component (e.g. an Application Programming Interface or video decoder). The act of a an author requesting the availability of a feature through a feature element is referred to as a feature request. 
The feature element serves as a standardized means to request the binding of an IRI identifiable runtime component to an application for use at runtime.
Using a feature element denotes that, at runtime, an application can attempt to access the feature identified by the feature element's name attribute. 
How a user agent makes use of features depends on the user agent's security policy, hence activation and authorization requirements for features are beyond the scope of this specification.
A feature has zero or more parameters associated with it.

#### **2.8.1 Attribute**

##### **The `name` Attribute**

An IRI attribute that identifies a feature that is needed by an application at runtime (such as an API).

##### **The `required` Attribute**

A boolean attribute that indicates whether or not this feature has to be available to an application at runtime.

  - true - the required attribute denotes that a feature is absolutely needed by an application to function correctly,
    and without the availability of this feature an application serves no useful purpose or won't execute properly.
  - false - the required attribute denotes that an application can function correctly without the feature being supported or otherwise made available by the user agent.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <feature name="http://www.obigo.com/api/audio" required="false"> </feature>
</widget>
```

#### **2.8.2 The <param\> Element**

The param element defines a parameter for a feature. A parameter is a name-value pair that is associated with the corresponding feature for which the parameter is declared for.
A author establishes the relationship between a parameter and feature by having a param element as a direct child of a feature element in document order.

##### **The `name` Attribute**

A string attribute that denotes the name of this parameter.

##### **The `value` Attribute**

A string attribute that denotes the value of this parameter.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <feature name="http://www.obigo.com/api/audio" required="false">
        <param name="version" value="1.1.1.0"></param>
    </feature>
</widget>
```

### **2.9 The < access > Element <a id="id-access-element"></a>**

The access element defines the security model controlling network access from within an application,
as well as a method for authors to request that the user agent grant access to certain network resources or sets thereof.

#### 2.9.1 Attribute

##### **The `origin` Attribute**

An IRI attribute that defines the specifics of the access request that is made. Only the scheme and authority components can be present in the IRI that this attribute contains (\[URI\],\[RFC3987\]).
Additionally, an author can use the special value of U+002A ASTERISK (\*). This special value provides a means for an author to request from the user agent unrestricted access to network resources.

##### **The `subdomains` Attribute**

A boolean attribute that indicates whether or not the host component part of the access request applies to subdomains (as defined in \[RFC1034\]) of domain in the origin attribute.
The default value when this attribute is absent is false, meaning that access to subdomains is not requested.</span>


```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <access origin="https://www.obigo.com" subdomains="true" />
    <access origin="https://api.obigo.com:9292" />
</widget>
```

### **2.10 The < thumbnail > Element<a id="id-thumbnail-element"></a>**

The icon element represents a custom thumbnail image for an application. \[AF Extension Element\]</span>

#### **2.10.1 Attribute**

##### **The `src` Attribute**

A path attribute that points to a file inside the widget package.

##### **The `width` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred width for the thumbnail.

##### **The `height` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred height for the thumbnail.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <thumbnail src="thumbnail.png" subdomains="true" />
</widget>
```

### **2.11 The < depend-service > Element<a id="id-depend-service-element"></a>**

The depend-service element defines the author's preferred service application for an application. \[AF Extension Element\]  
When an application starts, it's depend service will be started automatically by the framework. Zero or more service elements can be placed as child elements.

#### **2.11.1 The <service\> Element**

The service element represents a service application.

##### **The `id` Attribute**

An IRI attribute that denotes an identifier for a service application.
It's `mandatory` for authors to use id attribute with a widget element.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <depend-service>
        <service id="http://www.obigo.com/common/servcie_app1" />
        <service id="http://www.obigo.com/common/servcie_app2" />        
    </depend-service>
</widget>
```

### **2.12 The < gadgets > Element<a id="id-gadgets-element"></a>**

The gadgets element defines provided gadget application through the widget package. \[AF Extension Element\]. 
One or more gadget elements can be placed as child elements.  
Authors are strongly encourage to package gadget files within 'gadgets' directory.

#### **2.12.1 The <gadget\> Element**

The gadget element represents a gadget.

##### **The `size` Attribute**

A keyword denotes the gadget size for each device brand. It's `mandatory` for authors to use gadget attribute with a gadget element.

**Gadget size**

| Gadget Size | Renault <br> 7P Landscape  | Renault <br>9P Portrate | Dacia<br> 7P Landscape | Nissan* <br>9P Landscape |
|--|--|--|--|--|
|"S"  | 192*178  | 194*191 | 192*178 | 154*154 |
|"M"  | 390*178  | 396*191 | 390*178 | 410*199 |
|"L"  | 390*362  | 396*390 | 390*362 | 410*455 |
|"LR"  | -  | 800*191 | - | - |
|"XL"  | -  | 598*390 | - | - |
|"XXL"  | -  | 800*390 | - | _ |


**INFO: Nissan Gadget is provided since the Application Framework v1.6.15.**

#### **The `description` Attribute**  

The description attribute represents a human-readable description of the gadget.
Each gadget contents has to be placed into below

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <gadgets>
        <gadget size="S" description="gadget description strings"></gadget>
        <gadget size="L" description="gadget description strings"></gadget>        
    </gadgets>
</widget>
```

##### **2.12.1.1 The <content\> Element**

The content element is used by an author to declare which custom start file the user agent is expected to use when it instantiates the gadget.  
It's `mandatory` for authors to use content for a gadget element.

##### **The `src` Attribute**

A path attribute that allows an author to point to a file within the widget package.

##### **The `type` Attribute**

A media type attribute that indicates the media type of the file referenced by the src attribute.

##### **2.12.1.2 The <preview\> Element**

##### **The `src` Attribute**

A path attribute that points to a file of size inside the widget package.

##### **The `width` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred width for the thumbnail.

##### **The `height` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred height for the thumbnail.

##### **2.12.1.3 The <shortcut\> Element**

##### **The `src` Attribute**

A path attribute that points to a file inside the widget package.

##### **The `width` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred width for the thumbnail.

##### **The `height` Attribute**

A numeric attribute greater than 0 that represents, in CSS pixels \[CSS\], the author's preferred height for the thumbnail.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <gadgets>
        <gadget size="S" description="gadget description strings">
            <content src="gadgets/s/index.html" type="text/html" />
            <preview src="gadgets/s/preview.png"  />
            <shortcut src="gadgets/s/shortcut.png"  />
        </gadget>        
    </gadgets>
</widget>
```
 

### **2.13 The < intent > Element<a id="id-intent-element"></a>**

The intent element defines the operator information to navigate the specific application by device System.
\[AF Extension Element\]. This element is provided since the Application Framework v1.6.15.  
This element is used to define Alliance \*ePOI Booking interface.

**INFO: **  
ePOI Booking - If intent defined, the Application Framework sends intent data to Native HMI for Native Map application integration. 
If intent data is integrated in device system, the icon of intent data shall be displayed on the Native Map application.

#### **2.13.1 The <data\> Element**

##### **The `id` Attribute**

A numeric attribute that denotes an intent identifier inside the widget package. It's `mandatory` for intent element.

##### **The `value` Attribute**

A string attribute that denotes an intent operator.

##### **The `icon` Attribute**

A path attribute that points to a file inside the widget package.

##### **The `latitude` Attribute**

The latitude of the location in degree. The coordinates range from -90 to 90 degrees.

##### **The `longitude` Attribute**

The longitude of the location in degree. The coordinates range from -90 to 90 degrees.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <intent>
        <data
            id="1"
            value="intent_01"
            icon="intent1.png"
            latitude="37.211111"
            longitude="127.211111" 
        />
        <data
            id="2"
            value="intent_02"
            icon="intent2.png"
            latitude="38.311111"
            longitude="128.311111" 
        />
    </intent>
</widget>
```

### **2.14 The < meta-data > Element<a id="id-meta-data-element"></a>**

The meta-data element defines the widget package information. \[AF Extension Element\]

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <meta-data>
        ...
    </meta-data>
</widget>
```

#### **2.14.1 The <manifest-version\> Element**

The version of the manifest : “\[0-9\].\[0-9\].\[0-9\]”. This will be set by Obigo Studio.

```xml
<meta-data>
    <manifest-version>1.3.2</manifest-version>
</meta-data>
```

#### **2.14.2 The <store-id\> Element**

An identifier of an application in App Store. : "\*\[0-9\]\* | \*\[A-Z\]\* | \*\[a-z\]\* | \*-\* |\* \_\* | \*.\* ".  
It's `mandatory` element for the widget package update through SOTA.

```xml
<store-id>OBIGO.COM.RENAULT.APP1</store-id>
```

#### **2.14.3 The <license\> Element**

The license element represents a license permission. This is required information by Alliance Renault.

```xml
<license> secure permission </license>
```

#### **2.14.4 The <speech\> Element**

The speech element defines the author's preferred voice recognizable identifier for an application.

##### **2.14.4.1 The <name\> Element**

The name element defines the author's preferred user friendly name for an application

##### **2.14.4.2 The <phoneme-data\> Element**

The phoneme-data element defines the name with IPA Unicode.  
It's `mandatory` for speech element.

##### **The `phoneme` Attribute**

The L\&H+ format unicode attribute represents unicode string for the name.

##### **The `langcode` Attribute**

The language code attrubute represents language for the name.  
: languange code(ISO 639-3) + contry code(ISO 3166-3)</span>

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <meta-data>
        <speech>
            <name>weather</name>
            <phoneme-data phoneme="wéðər" langcode="en" />
            <phoneme-data phoneme="jour-là" langcode="fr" />
        </speech>
    </meta-data>
</widget>
```

#### **2.14.5 The <resource-usage\> Element**

The resource-usage element defines the authors' preferred resource usage for an application. This meta information is required by Renault.

##### **2.14.5.1 The <cpu\> Element**

The cpu elements defines the author's preferred cpu usage size -byte- for an application.

##### **2.14.5.2 The <ram\> Element**

The ram elements defines the author's preferred memory usage size -byte- for an application.

##### **2.14.5.3 The <storage\> Element**

The storage elements defines the author's preferred storage usage size -byte- for an application.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <meta-data>
        <resource-usage>
            <cpu>80</cpu>
            <ram>40960</ram>
            <storage>8192</storage>
        </resource-usage>    
    </meta-data>    
</widget>
```

#### **2.14.6 The <driving-restriction\> Element**

The driving-restriction element defines the author's preferred restriction rule while driving for an application.  
Regarding the restriction, an Application may require to define contents layout according to driving status.  
To recognize driving status, Javascript Application Interface 'EventHandler onChangedLockoutStatus' shall be taken in an application.
The EventHandler is used to get lockout status according to vehicle driving. (For the usage, please refer to AppAPI manual)

#### **The `content` Attribute**

The type of restriction attribute represents driving rule for the widget.

  - allowed:fully - The author preferred an application to be started and running without any restriction while driving.
  - allowed:partially - The author preferred an application to be started and running with some restricted content layout while driving.
  - forbidden:close - The author preferred an application not to be started an running while driving. Regarding the restriction, 
    the Application Framework makes an application not available to start and, if an application has already been run the Application Framework makes an application going to background running.
  - forbidden:disable - The author preferred an application to be displayed with fully restricted content layout while driving.

```xml
<widget 
    xmlns="http://www.w3.org/ns/widgets"
    id="http://www.obigo.com/oem/common/app1"
    version="1.0.0"
    viewmodes="fullscreen"
    group="utility"
>
    <meta-data>
        <driving-restriction content="allowed:partially" />   
    </meta-data>    
</widget>
```
