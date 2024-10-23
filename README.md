![npm](https://img.shields.io/npm/v/@taitems/jquery-gantt)
## [Demo and Documentation](http://taitems.github.com/jQuery.Gantt/)

## Installation

- Git clone
- `yarn add @taitems/jquery-gantt`, or
- `npm install @taitems/jquery-gantt` 

## About

jQuery Gantt Chart is a simple, easy-to-use chart that implements Gantt chart functionality as a jQuery component. This fork introduces several improvements and new features, while maintaining backward compatibility with the original plugin.

Forked from: [https://github.com/taitems/jQuery.Gantt](https://github.com/taitems/jQuery.Gantt)

## Features

The Gantt chart is capable of:

- Reading JSON data
- Paging results
- Displaying different colors for each task
- Showing short descriptions as tooltips
- Marking holidays
- Supporting multiple time scales, including hours, days, weeks, and months

## Compatibility

The plugin has been tested and should work on the following browsers:

 - Firefox 4+
 - Chrome 13+
 - Safari 5+
 - Opera 9+
 - IE 8+

## New Features and Improvements

This fork includes the following enhancements:

### 1. Per-instance Settings Storage:

Previously, the settings object was shared across all instances, which made it difficult to handle multiple Gantt charts with different configurations on the same page. To solve this:

Per-instance settings are now stored using jQuery's `.data()` method.
A new method `$.fn.gantt.getSettings(element)` allows you to retrieve settings for a specific Gantt chart instance by passing a selector.

Example usage:
```javascript
$("#ganttChart1").gantt({ scale: "days" });
$("#ganttChart2").gantt({ scale: "months" });

// Retrieve settings for #ganttChart1
var settings1 = $.fn.gantt.getSettings("#ganttChart1");
console.log(settings1.scale); // Output: "days"
```

### 2. Additional Parameters in Progress Bar Creation:

The `createProgressBar` function has been enhanced to support three new parameters:

- `tractionId`
- `fqid`
- `url`

These allow for more detailed customization and interaction with the progress bars.

### 3. Extended onRender Callback:

The `onRender` callback has been updated to include the following settings as parameters:

- `scale`
- `source`
- `holidays`
- `itemsPerPage`

This ensures that the current configuration is available whenever the Gantt chart is rendered, allowing developers to better respond to different rendering scenarios.

### 4. Consistency in Callback Comments:

To improve code clarity, the comments for `onItemClick` and `onAddClick` callbacks have been aligned to be consistent with the actual function signatures. This helps ensure that developers understand the expected parameters and return values.

### 5. Hourly Scale Enhancements:

When zooming in to the hourly scale, a new CSS class, `hour`, is added to the time cells in the Gantt chart. Additionally:

- The CSS for the `hour` class has been updated to provide styling similar to the `day` class, ensuring a uniform appearance across different zoom levels.

## Example Usage

Basic example to create a Gantt chart:

```javascript
$("#ganttChart").gantt({
    source: [
        {
            name: "Task 1",
            desc: "Description of task",
            values: [
                {
                    from: "/Date(1609459200000)/",
                    to: "/Date(1612137600000)/",
                    label: "Task 1",
                    customClass: "ganttRed"
                }
            ]
        }
    ],
    scale: "days",
    itemsPerPage: 10,
    onRender: function(data) {
        console.log("Current scale:", data.scale);
    }
});
```

## License

Distributed under an MIT license.