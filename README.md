# Data Normalization

**ID**: `normalization`  
**Version**: 1.0.0  
**Category**: preprocessing  
**Author**: CauldronGO Team

## Description

Normalize data using various scaling methods

## Runtime

- **Type**: `python`
- **Script**: `normalization.py`

## Inputs

| Name | Label | Type | Required | Default | Visibility |
|------|-------|------|----------|---------|------------|
| `input_file` | Input File | file | Yes | - | Always visible |
| `columns_name` | Sample Columns | column-selector (multiple) | Yes | - | Always visible |
| `scaler_type` | Scaler Type | select (minmax, standard, robust, quantile, normalizer, power) | Yes | minmax | Always visible |
| `with_centering` | With Centering | boolean | No | false | Visible when `scaler_type` = `standard` |
| `with_scaling` | With Scaling | boolean | No | true | Visible when `scaler_type` = `standard` |
| `n_quantiles` | Number of Quantiles | number (min: 100, max: 10000, step: 100) | No | 1000 | Visible when `scaler_type` = `quantile` |
| `output_distribution` | Output Distribution | select (uniform, normal) | No | uniform | Visible when `scaler_type` = `quantile` |
| `norm` | Normalization Method | select (l1, l2, max) | No | l2 | Visible when `scaler_type` = `normalizer` |
| `power_method` | Power Transform Method | select (yeo-johnson, box-cox) | No | yeo-johnson | Visible when `scaler_type` = `power` |

### Input Details

#### Input File (`input_file`)

Data file to normalize


#### Sample Columns (`columns_name`)

Select columns to normalize

- **Column Source**: `input_file`

#### Scaler Type (`scaler_type`)

Normalization method to use

- **Options**: `minmax`, `standard`, `robust`, `quantile`, `normalizer`, `power`

#### With Centering (`with_centering`)

Center the data before scaling


#### With Scaling (`with_scaling`)

Scale the data to unit variance


#### Number of Quantiles (`n_quantiles`)

Number of quantiles for quantile transformation


#### Output Distribution (`output_distribution`)

Distribution for quantile transformation output

- **Options**: `uniform`, `normal`

#### Normalization Method (`norm`)

Norm to use for normalizer scaler

- **Options**: `l1`, `l2`, `max`

#### Power Transform Method (`power_method`)

Method for power transformation

- **Options**: `yeo-johnson`, `box-cox`

## Outputs

| Name | File | Type | Format | Description |
|------|------|------|--------|-------------|
| `normalized_data` | `normalized.data.txt` | data | tsv | Normalized data matrix |

## Requirements

- **Python**: >=3.11
- **Packages**:
  - numpy>=1.24.0
  - pandas>=2.0.0
  - scikit-learn>=1.3.0

## Example Data

This plugin includes example data for testing:

```yaml
  input_file: diann/imputed.data.txt
  columns_name_source: diann/imputed.data.txt
  columns_name: [C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_01.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_02.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_03.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_01.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_02.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_03.raw]
  scaler_type: minmax
```

Load example data by clicking the **Load Example** button in the UI.

## Usage

### Via UI

1. Navigate to **preprocessing** → **Data Normalization**
2. Fill in the required inputs
3. Click **Run Analysis**

### Via Plugin System

```typescript
const jobId = await pluginService.executePlugin('normalization', {
  // Add parameters here
});
```
