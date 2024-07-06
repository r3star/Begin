import openpyxl as xl
from copy import deepcopy

def copy_user(file):
    wb = xl.load_workbook('filename.xlsx') # load workbook from file
    ws1 = wb['Sheet1']  # select first sheet in the workbook
    new_wb = deepcopy(wb)   # create a copy of original workbook to avoid modifying it
    for row in range(2,ws1.max_row+1):
        if 'user' in ws1[f'A{row}']:  # check if user is mentioned in column A (assuming that)
            new_wb['Sheet2'].append([cell.value for cell in ws1[f'A{row}:D{row}'])   # copy row to another sheet
    new_wb.save('newfile.xlsx')  
