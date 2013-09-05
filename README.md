# CSS / LESS Style Guide

### Scoping

We should try to use simple and short class names whenever possible. But in order for this to work, we must always be sure our style definitions are apporpriately scoped. Inadequate scoping will result in styles for different elements bleeding over.

Files should be scoped to a specific unique container marked by `// Start scope` and `// End scope`.

    // Start scope
    #app .settings .edit-profile {
      

    // End scope
    }

### Organization and commenting

The first part of the file is general labeled `STRUCTURE`. Here we define general styles for positioning the larger element blocks within our scope. To save one level of indentation, it's not required to indent between the scopes.

    // Start scope
    #app .settings .edit-profile {
      
    // ============================  STRUCTUR
    .settings-column {
      width: 450px;
      float: left;
    }
    .language-settings-column { 
      float: right;
      width: 200px;
    }
    .modal-footer {
      clear: both;
    }

    // End scope
    }

Files are generally seperated into sections that seperate the major parts of the elemnt we're styling. For example, for the edit-profile page, We have STRUCTURE, PROFILE PICTURE, and FIELDS.

    // Start scope
    .settings .edit-profile {

    // ============================  STRUCTURE
    .settings-column {
      width: 450px;
      float: left;
    }
    .language-settings-column { 
      float: right;
      width: 200px;
    }
    .modal-footer {
      clear: both;
    }

    // ============================  PROFILE PICTURE
    .profile-image {
      background-size: 100px 100px;
      width: 100px;
      height: 100px;
      margin: 20px;
      float: left;
    }
    h3 {
      float: left;
      margin: 28px 300px 0 0;
      font-size: 18px;
    }
    #upload {
      .clearfix;
      text-align:center;
      border-bottom: 1px solid #e4e4e4;
      margin-bottom: 10px;
      .upload-progress {
        float:left;
        width:300px;
        margin-top:10px;
        .progressbar {
          display:none;
          width:300px;
          height:20px;
        }
        .bar { height: 20px; }
        .text {
          line-height:40px;
          padding:5px;
          font-weight:bold;
        }
      }
    }

    // ============================  FIELDS
    .settings-row {
      padding: 20px;
      table {
        tr td {
          padding: 5px 10px 5px 0;
          min-width: 130px;
          &:first-child { text-align: right; }
        }
      }
      input {
        .rounded(4px);
        .gradient-y(#efefef, #fff);
        border: 1px solid #d5d5d5;
        padding: 4px;
        width: 200px;
        font-size: 14px;
      }
      #country { width: 200px; }
    }

    // End scope
    }

### Mixins

We use a variety of mixins. Most commonly used are: clearfix, rounded (and also rounded-left, rounded-left-bottom, etc), gradient-y, gradient-x, transition, box-shadow, box-shadow-inset, etc. A lot of these are for CSS3, so we can isolate the mess of vendor prefixes into our mixin file. We also use mixins for buttons (blue-button, gray-button, facebook-button, etc).

Mixins are defined in /less/common/mixins.less

Mixin definitions should always be at the top of your style definitions. Example:

    .box {
      .clearfix.
      .rounded(5px);
      .gradient-y(#fff, #000);
      width: 500;
      float: left;
      margin: 20px;
      a.submit {
        .blue-button;
        float: right
        margin: 10px;
      }
    }

### Other general CSS guidelines

* Always put a space after the colon: `margin: 20px` not `margin:20px`
* Make sure styles are adequately scoped
* Try to abstract all CSS3 that require vendor prefixes into mixins
* Major elemnts within your scope should be seperated into sections to aid readability
* Less styles should be nested in a way that is easy to understand, which minimizes the need for inline comments.
* Prefer using many files as opposed to having fewer, larger files. Most files are under 200 lines long
* Use dashes to seperate works `.foo-bar` not `.foo_bar`
* Use mixins for adding common styles, instead of definig a global class and adding the class to many elements. Ie. we should not add the .blue-button class direct to DOM elements. Use the mixin
* Always use `margin: 1px 2px 0px 0px` instead of defing left, right, etc seperately, unless you're only going to define one of the four directions.
* Generally avoid using IDs, unless for very low level elements like #app
* Avoid using `!important` whenever possible. 
