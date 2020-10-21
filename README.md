Drag and Drop
=============

Basic jQuery plugin to allow drag and drop:

* dragging
* dropping of dragged elements
* sorting of lists and other nested html structures (```ul```, ```ol```, ```div``` etc.)

This is a fork of https://github.com/gardiner/draganddrop with minor changes and added minified versions of the js and css files 

Requirements
------------

- jQuery



Usage
-----

1. Include jQuery and draganddrop in document head:

    ```html
    <link href='draganddrop/dist/css/draganddrop.min.css' rel='stylesheet' type='text/css'/>
    <script src="https://code.jquery.com/jquery-3.2.1.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous"></script>
    <script src='draganddrop/dist/js/draganddrop.min.js' type='text/javascript'></script>
    ```

2. Create html structure:

    ```html
    <ul id="list">
        <li>Item 1</li>
        <li>Item 2
            <ul>
                <li>Subitem 1</li>
                <li>Subitem 2
                    <ul>
                        <li>Sub-Subitem 1</li>
                    </ul>
                </li>
            </ul>
        </li>
        <li>Item 3</li>
    </ul>

    <button id="drag">Drag me</button>
    ```

3. Initialize draggable and sortable:

    ```javascript
    $('#drag').draggable(/* options/callbacks or command */);
    $('#list').sortable(/* options/callbacks or command */);
    ```


Draggable
---------

Options and callbacks:

* ```handle``` (string) - selector of handle element (if null the complete element will be used as handle)
* ```delegate``` (string) - selector of delegate element (allows delegate-binding, delegate will be referenced as this in the event callbacks)
* ```revert``` (boolean) - if true the element reverts to its origin after dropping
* ```placeholder``` (boolean) - if true a transparent clone of the element is left at the origin while dragging
* ```droptarget``` (string) - selector for valid drop targets
* ```scroll``` (boolean) - if true the scrolling parent will be automatically scrolled while dragging
* ```update``` (function) - callback after dragging. Arguments: event, Draggable instance. This: draggable element.
* ```drop``` (function) - callback after dropping on valid droptarget. Arguments: event, droptarget element. This: draggable.element

Commands:

```javascript
$('#drag').draggable('destroy');
```

* ```destroy``` - deactivates the Draggable instance and unbinds all listeners


Limitations/Issues:

When ```placeholder``` or ```revert``` is set to true, click events on the draggable element would be swallowed by the generated clone. For most browsers (except Internet Explorer) this has been fixed by setting the clone to ```pointer-events: none;```.


Sortable
--------

Options and callbacks:

* ```handle``` (string) - selector of handle element (if null the complete element will be used as handle)
* ```container``` (string) - selector for container elements
* ```nodes``` (string) - selector for node elements
* ```autocreate``` (boolean) - automatically create nested containers within nodes
* ```group``` (boolean) - if true all elements in the jQuery object are grouped (items can dragged between them)
* ```scroll``` (boolean) - if true the scrolling parent will be automatically scrolled while dragging
* ```update``` (function) - callback after sorting. Arguments: event, Sortable instance. This: sortable element.

Commands:

```javascript
$('#list').sortable('serialize');
$('#list').sortable('destroy');
```

* ```serialize``` - returns an object representing the structure of the nested list
* ```destroy``` - deactivates the Sortable instance and unbinds all listeners

