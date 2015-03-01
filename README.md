# UCM-cdf2xml
Export text areas and metadata from Content Data files to XML. For importing into other systems. e.g. Drupal.
Written for Oracle Content 10g (prev. Oracle UCM), in Site Studio Designer.


Quick Notes:
- This is checked in with metadata "Web Site Object Type: Page Template" and part of the site you are exporting from.
- Modifications will be required to work, to match your metadata model and page structures.
- Do not run in Contribution mode, it will add junk to content areas.
- For the 'body' export, there is a dirty 'elseif' block that will insert the region definition that matches the current content type. This will need to be changed to suit your placeholders.

Usage:
- The page accepts either a standard content search query or a 'batch' value.
- The batch value matches a pre-filled metadata field (xBatchID). This field was pre-populated using a mass metadata updater in groups of 200, this helps to work around the server search limits.
- Batches were grouped by Content Type. With Groups > 200 seperated my numbers. ie. for Landing pages 'batch_land'. For Media Releases 'batch_mr_01', 'batch_mr_02'..
- This allowed a catch all to find missed or newly added items "QueryText=<NOT>(xBatchID <starts> `batch`)"


Issues:
- While nodeids are included, this does not export the site hierachy.
- Content searches are limited to 200 returned items. Steps must be made to work around this (discussed above)
- This was created quickly, for a single run. It is not pretty.
